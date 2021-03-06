---
layout: post
title:  "面向对象六大原则"
date:   2019-11-15 00:00:00
catalog:  true
tags:
    - java
    - 面向对象
    - 设计原则
---



## 1 概述

在设计面向对象的程序时，如果能遵循一些指导原则取设计，那么所设计的软件架构的灵活性和代码的可读性将会大大的提高，常用的面向对象原则有：单一职责原则、开闭原则、里氏替换原则、依赖倒置原则、接口隔离原则和迪米特原则等。

## 2 单一职责原则

就一个类而言，应该仅有一个引起它变化的原因。简单来说，一个类中应该是一组相关性很高的函数、数据的封装。但这个原则并不是总是那么清晰，很多时候一个类中很难做到单一职责，需要靠个人的经验来界定。
单一职责原则的好处如下：

- 可以降低类的复杂度，一个类只负责一项职责，这样逻辑清晰明了
- 提高类的可读性和系统的维护性，因为不会有其他奇怪的方法来干扰我们理解这个类的含义
- 当发生变化的时候，能将变化的影响降到最小，因为只会在这个类中做出修改

## 3 开闭原则

开闭原则的定义是：软件中的对象(类、模块、函数等)应该对于扩展是开放的，但是，对于修改是封闭的。它指导我们如何简历一个稳定的、灵活的系统。

软件开发过程中，产品需要不断升级、维护，修改原有的代码就有可能引发其他问题。开闭原则认为，程序一旦开发完成，程序中一个类的实现只应该因错误而被修改，新的或者改变的特性应该通过新建不同的类实现，新建的类可以通过继承的方式来重用原类的代码。显然，该原则提倡实现继承，已存在的实现类对于修改是封闭的，但是新的实现类可以通过覆写父类的接口应付变化。

 要做到开闭有两个要点：

- 抽象是关键，一个系统中如果没有抽象类或接口系统就没有扩展点
- 封装可变性，将系统中的各种可变因素封装到一个继承结构中，如果多个可变因素混杂在一起，系统将变得复杂而换乱 

## 4 里氏替换原则

里氏替换原则定义：所有引用基类的地方必须能透明地使用其子类的对象。

面向对象的语言的三大特点是继承、封装和多态。里氏替换原则就是依赖于继承和多态这两大特性。里氏替换原则通俗来讲，只要父类能出现的地方子类就可以出现，而且替换为子类也不会产生任何错误或异常，使用者根本就不需要知道是父类还是子类。但是反过来就不成立：有子类出现的地方，父类未必就能适应，因为子类可以扩展父类。

里氏替换原则的核心原理是抽象，抽象又依赖于继承这个特性，在面向对象当中，继承的优点和缺点都很明显，优点如下：

- 代码重写，减少创建类的成本，每隔子类都拥有父类的方法和属性
- 子类和父类基本上相似，但又与父类有所区别
- 提高代码的可扩展性

继承的缺点：

- 继承是侵入性的，只要继承就必须拥有父类的所有属性和方法
- 可能造成子类代码冗余、灵活性降低，因为子类必须拥有父类的属性和方法

里氏替换原则通俗的去讲就是：子类可以去扩展父类的功能，但是不能改变父类原有的功能。他包含以下几层意思：

- 子类可以实现父类的抽象方法，但是不能覆盖父类的非抽象方法。
- 子类可以增加自己独有的方法。
- 当子类的方法重载父类的方法时候，方法的形参要比父类的方法的输入参数更加宽松。
- 当子类的方法实现父类的抽象方法时，方法的返回值要比父类更严格。

里氏替换原则之所以这样要求是因为继承有很多缺点，他虽然是复用代码的一种方法，但同时继承在一定程度上违反了封装。父类的属性和方法对子类都是透明的，子类可以随意修改父类的成员。这也导致了，如果需求变更，子类对父类的方法进行一些复写的时候，其他的子类无法正常工作。所以里氏替换法则被提出来。
确保程序遵循里氏替换原则可以要求我们的程序建立抽象，通过抽象去建立规范，然后用实现去扩展细节，里氏替换原则和开闭原则往往是相互依存的。

## 5 依赖倒置原则

依赖倒置原则指代了一种特定的解耦形式，使得高层次的模块不依赖于低层次的模块的实现细节的目的，依赖模块被颠倒了。依赖倒置原则有以下几个关键点：

1. 高层次模块不应该依赖低层次模块，两者都应该依赖其抽象。
2. 抽象不应该依赖细节
3. 细节应该依赖抽象

在Java语言中，抽象就是指接口或抽象类，两者都是不能直接呗实例化的；细节就是实现类，视线接口或继承抽象类二产生的类就是细节，其特点是，可以直接被实例化，也就是可以加上一个关键字new产生一个对象。高层次模块就是调用端，低层次模块就是具体的实现类。依赖倒置原则在Java语言中的表现就是：模块间的依赖通过抽象发生，实现类之间不发生直接的依赖关系，其依赖关系是通过接口或抽象类产生的。

如果类与类直接依赖于细节，那么他们之间就有直接的耦合，当具体实现需要变化时，意味着要同时修改依赖者的代码，这限制了系统的可扩展性，降低了系统的灵活性。

## 6 接口隔离原则

接口隔离原则定义：客户端不应该依赖它不需要的接口。另一种定义是：类之间的依赖关系应该简历在最小的接口上。接口隔离原则将非常庞大、臃肿的接口拆分成更小的和更具体的接口，这样客户将会只需要知道他们感兴趣的方法。接口隔离原则的目的是系统解开耦合，从而容易重构、更改和重新部署。接口隔离原则说白了就是，让客户端依赖的接口尽可能地小。

## 7 迪米特原则

迪米特原则也称为最少知识原则。定义：一个对象应该对其他对象有最少的了解。通俗来讲，一个类应该对自己需要耦合或调用的类知道的最少，类的内部如何实现与调用者或者依赖者没关系，调用者或依赖者只需要知道他需要的方法即可，其他可一概不管。类与类之间的关系越密切，耦合度越大，当一个类发生改变时，对另一个类的影响也越大。

迪米特原则简单来说，只与直接的朋友通信。首先来解释一下什么是直接的朋友：每个对象都会与其他对象有耦合关系，只要两个对象之间有耦合关系，我们就说这两个对象之间是朋友关系。耦合的方式很多，依赖、关联、组合、聚合等。其中，我们称出现成员变量、方法参数、方法返回值中的类为直接的朋友，而出现在局部变量中的类则不是直接的朋友。也就是说，陌生的类最好不要作为局部变量的形式出现在类的内部。 

## 8 总结

 这些原则其实都是应对不断改变的需求。每当需求变化的时候，我们利用这些原则来使我们的代码改动量最小，而且所造成的影响也是最小的。但是我们在看这些原则的时候，我们会发现很多原则并没有提供一种公式化的结论，而即使提供了公式化的结论的原则也只是建议去这样做。这是因为，这些设计原则本来就是从很多实际的代码中提取出来的，他是一个经验化的结论。怎么去用它，用好他，就要依靠设计者的经验。否则一味者去使用设计原则可能会使代码出现过度设计的情况。大多数的原则都是通过提取出抽象和接口来实现，如果发生过度的设计，就会出现很多抽象类和接口，增加了系统的复杂度，让本来很小的项目变得很庞大。