---
title: "Ocsp Stapling 和iOS界面卡顿问题"
date: 2020-04-29T17:25:42-04:00
showDate: true
draft: false
tags: ["blog", "https", "ocsp", "nginx"]
---

这个问题成功的吸引了我的注意。

起因：一个Flutter写的app在iOS上偶尔会发生了界面卡顿甚至冻结10多秒，但在Android正常。

开始这个问题没太引起重视，觉得是flutter的问题。但后来随着dart的[issue](https://github.com/dart-lang/sdk/issues/41519)里面报告的人逐渐多起来，看起来不是那么简单。不过非常令人迷惑的是这个现象只在iOS偶尔出现，Android从来不出现，这种不确定性使得重现和调试非常困难。

在issue里面发现报告的人大部分疑似是中国用户，之后发现有人提到更换了阿里云证书之后问题不再重现，这使得我们把问题方向放在https上。最终发现服务器的OCSP Stapling失效，造成了soft failure。之后的行为要看客户端实现，有的浏览器接受soft failure，不进行客户端检查，一切正常。但有一些客户端比如Safari会自己去检查了OCSP状态，从而造成界面无响应。检查nginx log发现ocsp.int-x3.letsencrypt.org请求超时，随后确认此域名遭到了DNS污染。

在服务器开启OCSP Stapling对于提升速度[帮助很大](https://blog.cloudflare.com/ocsp-stapling-how-cloudflare-just-made-ssl-30/)。所以无论如何也是应该开启的。

但是仍然有两个问题没有解释：

1. 为什么Android没问题，iOS有问题
2. 为什么有时候可以重现，有时候不可以重现

为了回答这几个问题，顺便找一个解决方案，我顺着读了一圈代码和协议，从nginx到openssl，从tls到ocsp。最后终于能回答这两个问题了。

<!--more--> 

1 Android没有问题的原因是，[Google不满意ocsp这个解决方案](https://blog.wirelessmoves.com/2015/03/ocsp-stapling-and-android-that-doesnt-care.html)，所以所有google的产品，无论是android还是chrome都不进行ocsp检查。

ocsp作用是检查证书状态，尤其是是否吊销，Google认为检查证书状态并不能增加安全性，并且导致https请求时间变长，并且ocsp服务器本身也可能会出问题，这不是一个可靠的方案。Google通过分发一个列表到本地来解决证书检查问题。当然有人提出争议说分发列表这个过程会因为升级服务器被屏蔽而失效，Google认为如果能屏蔽我们的升级服务器，那么屏蔽ocsp服务器岂不是更容易？所以从2012年开始，Google就逐步取消了ocsp检查。

2 为什么有时候可以，有时候不可以

[读nginx代码](https://github.com/nginx/nginx/blob/c17bc31d41a0372002115899a2c64e89aeca7e7d/src/event/ngx_event_openssl_stapling.c#L554)，发现nginx会把ocsp请求结果放在内存里面，直到过期之前才会再次请求ocsp服务器更新状态。但是如果重启了nginx，内存里面的结果就丢掉了，下一次就会直接请求ocsp服务器。

letsencrypt使用akamai cdn分发ocsp状态，实际上遭到DNS污染的似乎是akamai.net的某一部分节点，应该还有少量没被污染。所以有时候还能取得正确的结果，一旦取得正确的结果之后，在下次nginx重启/ocsp过期之前就会变得一切正常。这使得重现它更加困难。

代码读完之后，也就知道了解决方案：

* 使用 ssl_stapling_file 配置，从一个外部文件获取ocsp信息 ngx_ssl_stapling_file 
* 使用 [ssl_stapling_responder](https://github.com/nginx/nginx/blob/c17bc31d41a0372002115899a2c64e89aeca7e7d/src/event/ngx_event_openssl_stapling.c#L382)配置，nginx会用这个设置覆盖证书里面的Authority Information Access信息，使得请求ocsp被发送到设置的服务器

两者之间我更倾向后者，后者灵活的多，也省去了跨机器更新文件的麻烦，顺便还能解决以后其它麻烦。

我首先想按照ocsp协议写一个简单的responder，不过搜索之后发现有人很多年前写过一段非常简单的[转发代码](https://github.com/dlecorfec/ocsp-proxy)，直接把请求转发给指定的服务器。虽然必须要设置一个固定的转发服务器（因为原始的Authority Information Access信息被nginx覆盖了）。我想更好的解决方案是修改一下nginx的代码，在这个http请求中把原始的AIA放到header里面一起发给代理，不过考虑到大部分人都会把所有证书集中在一个供应商，设置一个转发地址完全能解决问题。而且避免每次升级给nginx重新打补丁的麻烦。所以就不改了。

我稍微修改了一下这个代码，让程序可以从环境变量获得转发地址，以便于使用docker部署。新的代码在这里： https://github.com/virushuo/ocsp-proxy

部署好了之后在nginx.conf里面增加配置:

```
ssl_stapling on;
ssl_stapling_verify on;
ssl_trusted_certificate /etc/ssl/ca-certs.pem;
ssl_stapling_responder http://YOUR_PROXY_IP:8080/; 
```
