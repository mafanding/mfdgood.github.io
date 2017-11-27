----
layout: post
title: "设计模式之工厂模式"
date: 2017-11-19
----

# 什么是工厂模式？ #
工厂模式可以分为以下三种类型：
*   简单工厂（不是真正意义上的设计模式）
*   工厂方法（定义了一个创建对象的接口，但由子类决定要实例化的类是哪一个。工厂方法让类实例化推迟到子类）
*   抽象工厂（提供一个接口，用于创建相关或依赖对象的家族，而不需要明确指定具体类）

面向对象的原则：
*   多用组合少用继承
*   针对接口变成，不针对实现编程
*   为交互之间的松耦合而努力
*   类应该对扩展开放，对修改关闭
*   依赖抽象，不是依赖具体类

要点：
*   所有的工厂都是用来封装对象的创建。
*   简单工厂虽然不是真正的设计模式，但仍不失为一个简单的方法，可以将客户程序从具体类解偶。
*   工厂方法使用继承：把对象的创建委托给子类，子类实现工厂方法来创建对象。
*   抽象工厂使用对象组合：对象的创建被实现在工厂接口所暴露出来的方法中。
*   所有工厂模式都通过减少应用程序和具体类之间的依赖促进解偶。
*   工厂方法允许类将实例化延迟到子类进行。
*   抽象工厂创建相关的对象家族，而不需要依赖他们的具体类。
*   依赖倒置原则，要避免依赖具体类，而要尽量依赖抽象类。
*   工厂模式帮助我们针对抽象编程，而不要针对具体类编程。

# 简单工厂的实现 #
code:

abstract class Fruit
{

    protected $name;

    public function getName()
    {
        return $this->name;
    }
}
class Apple entends Fruit
{
    public function __construct()
    {
        $this->name = "apple";
    }
}
class Pear entends Fruit
{
    public function __construct()
    {
        $this->name = "pear";
    }
}
class Banana entends Fruit
{
    public function __construct()
    {
        $this->name = "banana";
    }
}
class FruitFactory
{
    public function createFruit($name)
    {
        $fruit = null;
        if ($name == "apple") {
            $fruit = new Apple;
        } elseif ($name == "pear") {
            $fruit = new Pear;
        } elseif ($name == "banana") {
            $fruit = new Banana;
        }
        return $fruit;
    }
}

end
