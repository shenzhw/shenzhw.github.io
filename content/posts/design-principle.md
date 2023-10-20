---
title: "设计原则"
date: 2023-10-20T14:52:30+08:00
draft: true
---

SOLID

**单一职责原则**


**里氏替换原则**

原则思想：使用的基类可以在任何地方使用继承的子类，完美的替换基类。

描述：子类可以扩展父类的功能，但不能改变父类原有的功能。子类可以实现父类的抽象方法，但不能覆盖父类的非抽象方法，子类中可以增加自己特有的方法。

优点：增加程序的健壮性，即使增加了子类，原有的子类还可以继续运行，互不影响。

里式替换原则是用来帮助我们在继承关系中进行父子类的设计。

里氏替换原则（Liskov Substitution principle）是对子类型的特别定义的. 为什么叫里式替换原则呢?因为这项原则最早是在1988年，由麻省理工学院的一位姓里的女士（Barbara Liskov）提出来的。

里氏替换原则主要阐述了有关继承的一些原则，也就是什么时候应该使用继承，什么时候不应该使用继承，以及其中蕴含的原理。里氏替换原是继承复用的基础，它反映了基类与子类之间的关系，是对开闭原则的补充，是对实现抽象化的具体步骤的规范。

里式替换原则有两层定义:
定义1

> If S is a subtype of T, then objects of type T may be replaced with objects of type S, without breaking the program。
 如果S是T的子类，则T的对象可以替换为S的对象，而不会破坏程序。
 

定义2：

> Functions that use pointers of references to base classes must be able to use objects of derived classes without knowing it。
> 所有引用其父类对象方法的地方，都可以透明的替换为其子类对象
 

这两种定义方式其实都是一个意思，即：应用程序中任何父类对象出现的地方，我们都可以用其子类的对象来替换，并且可以保证原有程序的逻辑行为和正确性。

**依赖倒置原则**

**接口隔离原则**

**迪米特法则**

**开放封闭原则**

DRY

KISS

YAGNI