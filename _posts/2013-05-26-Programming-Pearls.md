---
layout: post
title: Read the Programming Pearls
tags: [software,SE,program,code]
category: Book
---

![Programming Pearls](/img/post/programmingpearls.jpg)&#12298;编程珠玑&#12299;这本书读完感觉很诡异，在读的过程中感觉很有收获，但是却说不清从书中获得了什么，好像什么也没读懂。说实话，很难对这本书归类，有时它告诉你的是实际操作的性能问题，有时又在讲算法或者数据结构。不过确切的说，它告诉我们的是一种无招胜有招的境界。无论是实际操作、算法还是数据结构都是在为项目服务的，我们的目的只有一个 - 完成项目。

一个项目与一个科研课题的区别就是它需要被实践，需要一种行之有效的解决方案。在一个系统被部署到实际环境中时，有时可能需要它无比精准，有时是快速运行，有时是超低成本，或者也有可能是兼而有之的权衡。此时工程师就需要调整一切可以调整的东西去满足这些需求，这些东西自然就是硬件环境、算法、数据结构了。作者Jon Bentley要告诉读者的就是这些调整所需要的手段。

第一部分讲的是基本操作，我的理解这部分讲的是“手段”，从算法、数据结构、程序设计到测试这样的细节，介绍了许多能影响实际部署结果的手法。而第二部分则是“效果”，是时间与空间的权衡，利用分析、估算确定性能，在算法设计和代码调优中节省成本开销。最后一部分则是介绍了一些实际的应用，通篇讲述的二分搜索，当然还有排序等，数据结构和基本类型也是一个重点。

其实这本书买了很久了，但是一直没怎么好好看过，主要是因为总觉得是在讲后端技术。但仔细阅读之后才感觉到了技术的相通，不在乎什么语言，什么时代。也许我一辈子也不会有机会去面对一个超大的系统部署的解决方面这样的问题，但只要还在写程序做项目，这些类似的问题就不会离去。

在前端开发中，IE就像一个性能奇差的老爷车般的大型机，要考虑它的性能与内存占用，有时需要函数节流，有时需要隐藏一些东西，还需要考虑图片的加载与缓存。而Webkit又几乎成为了移动互联网浏览器的代名词，需要考虑不同的交互，不同的操作习惯与视觉习惯体验，另外众多标准浏览器支持HTML5后，可以使用的手段越来越多。更重要的是，这些浏览器的差异，程序必须同时兼容，这对算法和数据结构的选择，时间与空间的权衡都是强大的考验。

比如说在以前的一个项目中，我面对的是4个没有规范的后端工程师提供的Ajax接口，然而时间不允许我逐一进行调用，如果是你会怎么做？很快我想到了一个解决方案，将接口名放入数组，然后通过数组下标将混乱的接口名变成了有序的数字。但是后来发现了一个Bug，这个问题有点严重了，由于在javascript中数组是引用类型，有点像指针的意思，所以当我把所谓的接口名传入Ajax封装方法中后，这个方法改变了引用的变量，然后这个接口名的数组的值也相应的改变了，很明显，结果是调用的接口失去了控制。随后我下意识的将这个数组每次获取的时候都复制了一遍，然后在IE6中，性能出现了问题，浏览器渲染就像结巴了一下，一跳一跳的，在chrome中测试发现效率比原来低了几倍。这时我无意识的使用了一个不错的手段，调整了数据类型和结构，采用字符串放置这些名称，然后使用下划线将不足的空位不足使所有接口名的长度一致，在使用的时候直接获取对应的区段，并利用正则去掉下划线，一切回复了正常。