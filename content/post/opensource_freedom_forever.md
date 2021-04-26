---
title: "开源是自由的，永远"
date: 2019-05-21T21:22:19-04:00
draft: false
tags: ["blog","tech", "internet", "opensource"]
---

开源软件到底受不受美国政府管制？会不会应美国政府的要求禁运？最近这个话题成了热点。遗憾的是，到现在中文文章里我没看到能把这个事情说清楚的文章，这让我非常惊讶。中国科技和互联网行业从开源软件中受益极大，也有无数直接和间接参与者，但是这些基本事实还是糊涂的，比较遗憾。

<!--more--> 

不卖关子，我先说结论，再来讲历史和过程。这个事情的奥秘在“开源软件”这四个字上，用一个不太精确的说法概括结论，“开源（源代码）”是受美国宪法第一修正案保护的言论自由，而“软件”是一种产品，受出口管制法律管制。所以看起来开源软件是一件事，其实它包含了两个不同的部分。无论任何许可证，无论是GPL还是Apache或是MIT，采用它们的代码都不会受到美国管制法律影响。但是分发尤其是分发编译打包之后的成品，那个叫做软件，软件就脱离了第一修正案保护的范围， 和大部分真实商品一样，适用于所有管制法律。所以丝毫不用担心有一天美国不允许别人使用源码，不允许别人使用Linux内核，这件事美国政府几乎是不可能做到的。


大多数人认为软件和源码是一回事，理解不了为什么它们适用法律完全不同？答案也很简单，源码被判定属于言论自由，这是一群美国工程师、科学家、法学家冒着生命危险和职业代价，和美国政府以及几大执法部门抗争而争取回来的权利。他们这么做是为了对抗把加密软件列入军火管制范围的法律，而为什么加密软件被算作军火管控？这要从历史说起。


我们要追溯到80年前，二战时期，那是计算机行业的祖师爷阿兰图灵活跃的时代，那个时候，今天我们所说的计算机还没有诞生，“图灵机”这个计算机的理论模型刚刚提出不久。尽管计算机还没有产生，但是机械驱动的加密机已经开始在军队中普及，纳粹德国使用的“Enigma”密码机就是其中最可靠的一种。为了破译德军密码，盟国各国都有相当大的投入，法国人贡献了情报，波兰数学家和密码学家贡献了破解理论…英国军情部门统筹了全局，图灵带领的小组在这里制造出了专门用来解密的“密码炸弹”破译机，最终使得盟军可以完全掌握德军情报，这和盟军取得二战胜利有密不可分的关系。不要认为这只是欧洲的事，亚洲战场上日本同样使用了德军的密码机。关于这段历史，70年代英国档案解密之后已经有无数作品讲述它，这里不说细节了。

![](/images/opensource_freedom_forever/Wartime_picture_of_a_Bletchley_Park_Bombe.jpg)

图灵的破译机密码炸弹照片

加密和解密技术伴随战争而生，产生于军方，它在很长历史时期内都被认为是军事产品，和武器一样被算作军火管制范围自然不意外。在这个时期，这些系统都是硬件,普通人也接触不到。从80年代开始，PC的兴起让软件加密和解密也开始发展，同时商业尤其是金融行业的发展，使得军事用途之外的密码需求急剧增加，于是美国政府开始放宽密码产品的管制范围，商业应用得以使用这些技术，但是超过40位密钥的加密产品，仍然出于被禁止出口的范围，要出口需要事先向美国政府申请许可，美国政府仍然把加密软件当作军火管理。


一转眼，时间到了1991年。程序员Phil Zimmermann写了第一个个人可以用的高强度加密软件，叫做PGP，PGP使用密钥长度大于128位，远远超过了美国政府的管制规定。之后他把源码放到互联网上让人们随便下载。既然放在了网上，自然就不是只有美国公民可以下载到了，当美国之外也有人下载的时候，这件事就惊动了美国政府。之后美国政府开始对他进行犯罪调查，这个调查使得Zimmermann在当时的技术和法律圈子瞬间出名，人们开始为他提供各种支持。之后Zimmermann决定通过美国宪法第一修正案对于出版自由的保护来规避这个问题，他通过MIT出版社出版了一本书，书的内容就是PGP的全部源码，买到书的人只需扫描和OCR全书，就可以得到PGP的代码，之后自己编译，就是可用的加密软件。技术和法律在此时发生了第一次碰撞，技术以极端灵活的特性顺利规避了法律制约，算勉强获胜。之后，一系列算法通过印刷品的方式发行，后来人们为了抗议这种管制方法，甚至用几行代码实现了RSA加密算法，然后把这些代码[印在T恤上](http://www.cypherspace.org/rsa/)，或者干脆当作纹身把代码纹在胳膊上招摇过市。虽然这个问题暂时绕过去了，但是越来越多的人开始考虑这个新问题：既然源代码印在书籍上，就算作言论自由，那么源代码本身能不能被算作言论呢，如果算的话，在网上发表源码，是否应该被第一修正案保护？


![](/images/opensource_freedom_forever/uk-front2.jpg)

图片：军火T恤，上面印着代码，写着“这件T恤被分类为军火，不能出口也不能给外国人看到”


![](/images/opensource_freedom_forever/tattoo3.jpg)

图片：“军火”代码纹身


时间继续推移，软件、互联网和计算机行业继续发展，越来越多的人遇到了类似的问题。开始有更多的人挑战出口管制法律。1995和1996年，连续出现两个案件，[Junger v. US Department of State](https://www.eff.org/ja/cases/junger-v-dept-state) 和 [Bernstein v. US Department of Justice](https://www.eff.org/cases/bernstein-v-us-dept-justice)，前者是大学教授Junger和美国国务院的诉讼，后者是加州伯克利大学的学生Bernstein和美国司法部之间的诉讼。这两个案例原因不同，诉讼对象也不同。 教授Junger是要在课上为学生讲述技术相关的法律，其中有关于软件加密的技术，但听课的学生中有外国留学生，因此也落入了出口管制限制的范围，并且面临了百万美金的巨额罚款和最高10年的刑期。学生Bernstein是为了公开发表自己发明的加密算法论文，并且希望可以公开的，不受限制的参加学术会议讨论他的算法。两个问题指向了同一个答案，软件源代码应该是一种言论自由，并且应该受宪法第一修正案保护。在电子前线基金会的帮助下，在大批律师和法学家、科学家、工程师的共同努力下，一直到2000年之后，最终的胜利终于到来，两个案例分别在第六巡回上诉法庭和第九巡回上诉法庭得到了同样的判决：软件源代码是言论自由，受宪法第一修正案的保护。特别值得注意的是，第九巡回法院和第六巡回法院分别位于美国西部和南部，两个相同的判决说明了，无论是自由派还是保守派，都持同样的结论。从此之后，美国政府再也不能试图限制软件源码流通了。


知道这些历史之后，很容易就可以得到确定的结论：美国政府没有能力对软件源代码实施禁运。无论是美国公民写的代码，还是其他国家人写的放在美国服务器上的代码，都一样，源代码永远是自由的。 那么为什么Apache许可证中会包含“可能受到美国出口法规管制”的字样，而GPL许可证根本没有这个内容呢？因为GPL是一种只管源代码的许可证，并且它有传染性，包含GPL的项目本身也必须开源，所有通过GPL许可证发布的产品必须提供代码，它根本不涉及分发和不开源的部分，也就不会被列入管制范围。但Apache/MIT/BSD之类的许可证不是强制开源，人们可以使用它发布不开源的代码，也可以在发行版本中混入不开源的二进制软件和库，这些不是代码的东西 ，就会落入管制范围。因此他们必须加上这个声明“可能受到美国出口法规管制”，这里说的是“存在这种可能性”，而不是说“一定如此“。


当然，这里有另外一个细节问题是，GPL只管源代码，那么如果一个组织开源了自己的代码，同时又提供二进制发行版，这时候会不会被管制？答案是会的。所以要做软件发行（而不是纯粹源代码发行），就需要在GPL基础上扩充出来一份新的许可证，这份许可证里面同样会写上“可能受到美国出口法规管制“字样。针对这个问题[RMS曾经亲自回答过](https://fedoraproject.org/wiki/FreeSoftwareAnalysis/FSF)：fedora许可证包含了“可能受美国出口法规管制“，这和GPL冲突吗？RMS的回答大意是：GPL只管源码是不是开源，其他都不管。你如果要打包发行GPL的软件，在履行了开源义务之后，GPL就不会找你麻烦了，之后你可以随便设定各种条件在你的发行版上，哪怕是“禁止蓝色头发的人使用“都可以，那是你自己的决定。这就是对源码和软件之间法律关系的最好解释。强制开源保证了自由，所有人都有机会使用它，不会受到任何限制。一个最极端的例子是这样，做为美国禁运的重点国家朝鲜也有自己的Linux系统，他们一样是自己拿源代码编译发行的版本。（当然，朝鲜并没有开源他们的红星Linux代码，是违反GPL授权的）


开源运动可以算是人类历史上最大的奇迹之一，来自世界各地的人，在不同的国家不同的制度下，用不同的语言，共同创造了一堆属于全人类，所有人都可以自由使用的工具。他们之间可能互相不能听懂对方说话，可能政治观点完全不同，甚至可能是完全敌对的，但是仍然共同为这个工程贡献了力量。我想不出来人类还有什么其他的事情达到过这样的高度和广阔程度。


大家关心的另外一个问题是git和Github会不会算在禁运范围内。首先要区分git和github是两个完全不同的东西，git是一套开源的软件代码版本控制系统，如上所述，它是完全自由的。Github是一个商业公司，提供git托管服务，所以Github确实有可能因为法律要求不提供某些地区的服务，比如朝鲜IP是不能访问Github的。但是这对于中国用户似乎完全不是问题，毕竟世界流量最大的100个网站里面大部分中国用户都不能访问。


Git本身就是一套分布式代码管理系统，你只要使用git，那么你自己的计算机上始终会有一份和服务器同步的代码版本，即使服务器拒绝你访问了，你也不会丢失源代码，自然也就不存在“抓紧备份一份代码”这种问题，代码本身就存在你的计算机上。


最后一个问题是，为什么这么多开源软件基金会都在美国？这个问题非常有趣，毕竟，开源软件最重要的作者们，其中至少有一半不是美国人，你看，Linux作者Linus  Torvalds是芬兰人，C++之父Bjarne Stroustrup是丹麦人，Python作者Guido van Rossum是荷兰人，Java作者James Gosling是加拿大人…更别说每个开源基金会都有大量的董事们不是美国人，也并不生活在美国。为什么他们不把基金会放在自己的国家而是放在美国？


除了美国有更丰富的资源这个理由之外，还有一个重要的理由，就是美国的制度可以保护他们的工作永远是开放的。这件事颇有一点中国太极的意味，美国在开源领域成为主要阵地，不是因为它强大，而是因为它不够强大，美国政府不是说一不二，想怎么做就怎么做的政府，它的错误可以被挑战，被纠正，可以和它法庭见…美国公司、美国人民、美国法律和美国政府，这些概念看似一样，实际上是不同的。他们有共同利益，但是也有冲突，同时又互相制约。有ACLU，EFF（电子前线基金会）这样的组织，几十年如一日挑战不合理的法律制度，和政府打官司，并且无数次获胜。这些复杂的关系构成了让开源软件发展的重要社会基础，人类社会没有什么100%确定的事情，但是这种互相制约的平衡最大概率上保证了这些项目的自由，这是世界各国开源项目领导者和参与者经过漫长时间之后的共识。


如果不相信这个看法，想想前面提到的几个案例，一个美国公民，希望让全世界人民都可以使用自己的算法和代码，而完全不管敌对国家会不会获得他的成果。一个美国教授，希望给外国留学生讲解加密技术，冒着自己坐10年牢的风险，拿起法律武器挑战美国政府，并取得了最后的胜利。这件事要发生在其他国家，会是怎么样的结局？被骂做卖国贼算是起步待遇吧？更别说还有很大可能会承受更糟糕的结果。但是在美国，他们不仅能获得胜利，美国人民还视他们为英雄。


我们还可以假设一个场景。如果真的发生美国政府试图禁止中国使用Linux内核这种事情，你猜谁会先站出来骂美国政府？显然是自由软件基金会的创始人RMS和Linux的作者Linus。他们不仅会骂，还会在法律上挑战美国政府，并且会把所有代码托管到其他国家。凡是以”有一天我们会用不了Linux内核“为借口搞什么独立系统的，我敬佩他们的勇气。但是一方面他们担心的事情不可能发生，另外一方面，做个操作系统在这个时代并不算难，难的是如何建立整个生态。软件和互联网生态是全球化的产物，整个生态的完成是全世界工程师和企业共同完成的，任何一个国家也难以独立建设完成一套生态，即使美国，它也不可能脱离世界独立存在。


回头看这个历史，开源运动和加密运动互相扶助完成的这个过程。密码学家始终扮演了重要的角色，被列入军火管制的东西是加密软件，这使得密码学家和法律制度发生了冲突，如果没有这种冲突，就没办法到法院挑战美国政府，也就没法拿到法院最终的判决。如果没有判决，源代码算不算一种言论自由就仍然是不确定的争议，那么开源运动就很难产生这样的影响力。如果没有开源运动，没有Linux，没有GCC，没有Android，没有浏览器…整个互联网可能都不会存在，那么软件和工具仍然会掌握在少数几家企业手里，距离普通人遥不可及。


密码学家们不仅改变了二战的进程，他们也一直通过各种方式影响着社会，加密运动参与者极端注重隐私和自由，虽然他们的很多努力只是是出于维护自由的目的，但他们的创造物则影响深远，虽然其中大部分并不为普通人所知，但每隔一些年，总会有一些成果产生了惊天动地的效果，被人们所知。最近的一次大概要算这件事：


2009年1月8日，有人在密码学圈子里面发了这么一条消息：


"I made the proof-of-work difficulty ridiculously easy to start with, so for a little while in the beginning a typical PC will be able to generate coins in just a few hours."


发布这条消息的人使用的名字是 Satoshi Nakamoto，在中文里，这个名字被译作“中本聪”。

-----

我之前可能提起过，我和几位朋友还有一个播客节目，我们也会近期用播客的形式再一起聊聊这件事。因为媒介的不同，涉及的内容也会有区别。当然，除了这些技术话题，我们也有其他好玩的话题聊。如果你喜欢听播客的话，欢迎订阅：

* 官方博客：https://jinjinledao.org
* 微博：@津津乐道播客
* 微信公众号：津津乐道播客
* Twitter：@jinjinledaofm
* Telegram 群：https://t.me/htnpodcast
* Telegram Channel：https://t.me/jinjinledao
