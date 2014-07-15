---
layout: post
title: 浅谈AngularJS模板
tags: [javascript, angular, angularjs, template]
category: Tech
---

作为最流行的MVVM（Model-View-View-Model）框架之一，相信大部分前端对AngularJS都不会陌生，我也一样久仰大名，不过要说真正的学习和使用AngularJS，还是从三个月前来到现在的项目开始的。不得不说，AngularJS所带来的改变是巨大的，被称为未来浏览器的模式一点也不为过，尤其是思维上的转变。

作为一个常年挥舞着jQuery去指挥无穷无尽的DOM的前端，初次接触AngularJS是有困难的，许多先贤警告我们不要在AngularJS中使用jQuery亦是如此。即使AngularJS中带有jQlite对象，也仅仅是为了弥补一些地方AngularJS的局限性。在深入学习之后，我渐渐的发现了这点。过去使用jQuery的前端就像一个操纵提线木偶的傀儡师，而手握AngularJS的前端简直是不折不扣的魔法师。我们不需要再根据数据去改变DOM，然后填入数据，我们所要做的仅仅是决定数据的表现形式后等待数据的注入。文档流中的元素就像活过来了一样，根据数据表现出了对应的样子。

这一切的核心除了匪夷所思的DOM监听机制，还有就是AngularJS的模板（template）以及其中多不胜数的内置指令（directive）了。因此，我将在本文中谈谈AngularJS的模板以及其思维模式。
<!-- more -->

### 模板中的内置指令

AngularJS模板和EmberJS的模板相比它比较普通，仍然是HTML格式的文件。这使得许多人并未真正了解AngularJS的模板，而仅仅认为AngularJS只是提供了一堆内置指令并可用于HTML文件。不过就先来说说这些内置指令吧，模板后面再详细讨论。

ngIf是个对于模板很重要的指令，它是基本的条件表达，满足条件时则存在，不满足则不存在。通过它可以轻松的让模板基于数据呈现不同结构。另外它会形成独立scope，这也是其与ngShow/ngHide的区别之一。如果ngIf出现太多可能会导致页面渲染速度降低，此时可以选择ngSwitch来代替它，不过我更建议检查你的逻辑。


ngRepeat则是另一重要指令，能循环创建DOM。可以说只要数据中有数组等结构，这一指令就必不可少。配合$index等索引变量，ngRepeat可以创造出多种形式的列表。还有ngRepeatStart/ngRepeatEnd可以将2个元素之间的内容循环创建，但我很少使用它们，因为这种混合多种元素的HTML结构不太好。

ngClass是样式层面上的主要指令，它的值可以是存放class名的变量，也可以是带有条件的对象。如此可以通过表达式来选择需要的class，以呈现不同的样式。ngHide与ngShow其实就是特殊的ngClass，ng-hide="[expression]"相当于ng-class="{'hide': [expression]}"。

这些基本的指令构成了一套很有效的模板逻辑，我们可以消除掉各种HTML的重复性代码，还能在单个模板中呈现出无数的形式。但我不赞成将大段的HTML做成partial或directive并通过switch或if来选择性呈现，因为模板应该是可复用的组件，而不是带有逻辑的路由。



### 真正的页面只有一个
### 反向思维的命名



模板原则：
1. 一个模板就是一个对象，不属于它的东西，无论多麻烦，即使HTML可以放在一起，也一定要排除在外，无论封装成directive还是partial或者分离出去；
1. 指令应该使用表达式，利用数据本身达到逻辑表达，而不是依赖于某一专用变量，比如使用data.length > 0而不是hasData。
1. 

