---
title: "google发布bigtable论文"
date: 2006-09-25T15:09:00+08:00
showDate: true
draft: false
tags: ["blog","tech","programming"]
---

8个人开发了2年半，现在bigtable的神秘面纱终于揭开了。google发布了一篇相当详细的论文“Bigtable: A Distributed Storage System for Structured Data ”

这篇论文内容空前详细，包括bigtable的目的，数据模型，一些实例api调用的代码，性能参数，还有和其他相关产品的比较。

如标题所述 ，bigtable是一个用来存储结构数据的分布式存储系统。与平时常用的数据库不同，bigtable并非一个支持sql语言的关系数据库，而是map方式的，列导向的数据库（一列数据连续存储）。bigtable为读进行了优化，对数据库的读取访问远远大于写入是互联网服务的重要特点。bigtable的时间特性也颇为引人注目，bigtable中数据都带有timestamp字段，可以保存不同时间的多个版本。

论文中提到，google已经有6个服务已经运行于bigtable上了。分别是：Google Analytics,Google Earth,Personalized Search,Google Finance, Orkut,Writely。这里面我觉得最值得注意的是Writely和Analytics，这两个都是google收购来的服务，通过一段时间的改造，已经重组了其架构，使他们成为可以承担海量负荷的大型服务。这似乎也标志了google对于Writely的重视。

特别值得注意的是，这6个服务都是恰好带有明显时间特性的服务，借助bigtable的时间特性，可谓如虎添翼。最近Google Earth也增加了时间的标签。将来，bigtable必将用于更多的地方，事实上，时间标签对于web服务是相当重要的特征，但由于数据量太大，保存困难，限制了很多应用的发展，bigtable应用于wiki或是archive.org之类的服务的时候，必将势如破竹。

以前我们分析过，google通过收购和内部创业等方式获得新型服务，然后通过强大的基础技术改造这些服务，使其成为高可用性，高负荷高稳定性的服务。这或许就是google未来的发展方向。google通过一系列的包装，使分布式数据库这样复杂的东西可以被简单的api调用，这无疑将大大提高google内部各小组的开发能力。

ps:感谢youfeng及时提供这个消息。

