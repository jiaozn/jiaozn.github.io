---
layout: post
title:  "学习php，看到__autoload介绍时我震惊了"
date:   2016-10-05 19:45:36 +0800 
categories: 编程
tag: php
---

* content
{:toc}



背景：我为什么要学php
========  

已经学习了`java`，以及`struts2+hibernate+spring`框架。期间作为对学习的检验，也使用`jsp/servlet/框架`实践出了几个系统，托管到`redhat`的`openshift`。然后就在犹豫下一步的学习方向，`php` or `ruby`?学习php是因为一个`“php是世界上最好的语言”`的笑话，还有扎克伯格的facebook最初也是php开发，还听过`wordpress、cms`等好多成熟、可套用的东西。想学习ruby是因为他是日本开发，据说是“程序员最好的朋友”，有个`ruby on rails`号称是“杀手级应用”，对这个神秘的语言充满好奇（如果还有需要理由，或许是我是白羊座，幸运石是红宝石Ruby）。

然后...前天发现`openshift`不在免费了。**不再免费了！**我反正是找不到一个承诺永久免费的java服务器了，这让我下定了必学php的决心。  

然后...  
=======  

直接看[php文档](http://php.net/docs.php)学习好像真的可以，没想到会这么完善（看到各种语言的mannuel版本时好震惊）。但总觉得有本书领着，会系统一些，提供给我一根开发的“知识线”，让我抓住重点。最终选的是《php从入门到精通（第三版）》。书看起来到时不慢，相对自学java时的痛苦，现在耳畔总会不自觉地有人说`“你有九阳神功护体，学什么武功都特别快”`...当看到pdf文件的Page298,教材的269时，对__autoload方法描述如下：  

> ...但还有一个问题是让开发人员头疼不已的，如果要在一个页面中引进很多的类，需要使用include_once()函数或require_once()函数一个个的引入。
> php5通过`__autoload()`方法解决了这个问题，`__autoload()`方法可以自动实例化需要使用的类。当称需要用到一个类，但该类还没有被实例化时，PHP5将调用`__autoload()`方法，在指定的路径下自动查找和该类名称相同的文件。如果找到，程序则继续执行；否则，报告错误。...
  

看到这里，我的第一反应是——这太逆天了！想到在java里要实现自动装配，需要借助spring，还要进行一大堆的设置，调试时候的`NullPointerException`，包冲突引起的注入异常，jdk原因造成的白白调试一下午...  

当然看到后面才知道，这个`__autoload`也没有那么“魔法”，也需要自己实现，但感觉要比“自己用陌生的jdk版本+陌生的spring版本+陌生的其他各种jar”，会不会因冲突导致不是自己原因的bug，完全没有底要好一千倍...  

结论  
========
我要把这门语言搞定！^_^
