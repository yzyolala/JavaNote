# Java 为什么受欢迎？

平台无关性：Java 具有平台无关性，这意味着它可以在安装有 Java 虚拟机（JVM）的任何操作系统或硬件平台上运行。这个特性使得 Java 在各种类型的应用程序中非常灵活和广泛使用，从桌面应用到移动和 Web 应用。

面向对象编程：Java 是一种面向对象的编程语言，这意味着它允许开发人员编写可重用的对象形式的代码。这使得代码易于管理，减少错误的机会，并使代码更加高效。

丰富的库和框架：Java 拥有广泛的库和框架集合，开发人员可以使用它们快速轻松地构建复杂的应用程序。这些库涵盖了广泛的功能，从数据库连接到 GUI 编程和网络。

安全性：Java 具有内置的安全功能，使其在 Web 应用程序中使用更加安全。它有一个安全管理器，可以控制对资源的访问并防止未经授权的访问。

社区支持：Java 拥有一个庞大而活跃的开发人员社区，他们分享知识和专业知识，提供支持，并为 Java 框架和库的开发做出贡献。这使得 Java 成为一种可靠和得到良好支持的开发语言。

# Define what is a Class and Object?

类是用于创建共享类似属性和行为的对象的蓝图或模板。它定义了一组属性和方法，描述属于该类的对象的特征和动作。

对象是类的一个实例。它是一个表示类的特定实例的运行时实体，具有由类定义的自己的属性和行为集。对象可以相互交互，并与外部世界交换消息。

总之，类定义了一组属性和行为，对象可以拥有这些属性和行为，而对象是一个类的具体实例，具有自己的独特值和行为集。

# Can a Java source file have more than one class? and more than one main method?

Java源代码文件可以有多个类，但其中只能有一个是public，且必须与文件名相同。其他类可以有任何访问修饰符（private、protected或默认的），并且可以有任何名称。

Java源代码文件中有多个main方法的问题，是不可能的。每个Java程序只能有一个main方法，这是程序的入口点。如果在Java源代码文件中定义了多个main方法，将会得到编译错误。

# What are OOPS concepts? Abstraction, Encapsulation, Inheritance, Polymorphism

OOPS stands for Object-Oriented Programming System, which is a programming paradigm that uses objects and their interactions to design and implement applications.

抽象：抽象是隐藏复杂实现细节并为用户提供更简单和必要信息的过程。通过抽象类和接口实现抽象。例如：自动取款机的安全性和易于扩展。

封装：封装是将操作数据的方法和数据封装在一个类中的技术。封装提供了数据隐藏，并确保数据仅通过类的定义方法访问，从而提高安全性和可维护性。

继承：继承是通过扩展现有类来定义新类的过程。新类继承现有类的所有属性和行为，并可以添加自己的属性和行为。通过使用“extends”关键字实现继承。继承允许子类使用父类中定义的属性和方法，也可以添加自己的属性和方法

多态性：通过方法重载和方法重写实现多态性。方法重载允许多个方法具有相同的名称但不同的签名，而方法重写允许子类提供其自己的实现，该方法已由其父类提供。

# Difference between String, StringBuffer and StringBuilder?

不可变性：String对象是不可变的，一旦创建了一个字符串对象，它的值就不能更改。StringBuffer和StringBuilder对象是可变的

线程安全性：StringBuffer是线程安全的，StringBuilder不是线程安全的，比StringBuffer更快。

性能：StringBuilder比StringBuffer更快，因为它不会产生线程安全的开销。

当字符序列的值不经常更改时应使用String，当多个线程时应使用StringBuffer，当单个线程时应使用StringBuilder。

# What is Constructor

构造函数是当一个类的对象被创建时调用的特殊方法。构造函数与类名相同，没有返回类型。

Java中有两种类型的构造函数：

默认构造函数：如果一个类中没有定义构造函数，则编译器会提供一个默认构造函数。它没有任何参数，仅使用默认值初始化数据成员。

带参数的构造函数：它是一个接受一个或多个参数并使用传递的值来初始化数据成员的构造函数。它允许我们基于传递的值创建具有不同初始状态的对象。

# Difference between keywords this vs super

"this" 关键字用于引用当前对象的实例变量或调用当前对象的方法。它可以用来避免变量名冲突。

"super" 关键字用于引用当前对象的父类。它可以用来访问父类的构造函数或方法。

总的来说，"this" 关键字是用来引用当前对象，而 "super" 关键字是用来引用父类对象。

# Public vs protected vs default vs Private modifiers

public成员：如果一个成员被声明为public，它可以从任何地方访问。类的可见性优先于成员的可见性。

default成员：如果一个成员被声明为默认成员，则我们可以在当前包中访问该成员，因此也称为包级访问。

protected成员：如果一个成员被声明为protected，则可以在当前包中的任何地方访问它，并且只能在外部包的子类中访问。

private成员：如果一个成员是私有的，那么我们只能在类内部访问该成员。

可访问性高度受限的顺序为：private > default > protected > public

public = anywhere 

protected = package + child classes of outside the package 

default = only within package 

private = only within class

# Difference between final, finally and finalize 

final 用于类、方法或变量：

当一个类被标记为 final 时，它不能被继承

当一个方法被标记为 final 时，它不能被覆盖

当一个变量被标记为 final 时，在初始化之后它的值不能被更改

finally 是一段无论是否抛出异常都会执行的代码块。通常用于释放资源，如文件、数据库连接或网络套接字。finally 块总是在 try 和 catch 块之后执行

finalize 是一种在对象被销毁之前由垃圾收集器调用的方法。应谨慎使用 finalize 方法，因为它可能导致不可预测的行为，并对应用程序的性能产生负面影响

总之，final 用于限制继承、方法覆盖和变量修改，finally 用于释放资源，finalize 用于在对象销毁之前执行终止任务

# What is a static and static block?

如果一个成员被声明为static，那么它直接属于类级别。你不需要实例化一个对象来使用它，而是可以直接通过调用它所属的类的名称来使用它。

静态代码块用于初始化静态成员变量。它只会执行一次，并且在类被加载时执行，优先于静态成员变量的初始化和静态方法的调用

```java
public class MyClass {
    // 静态成员变量
    static int num;
    
    static {
        // 静态代码块，初始化静态成员变量
        num = 10;
        System.out.println("静态代码块执行");
    }
    
    public static void main(String[] args) {
        // 访问静态成员变量
        System.out.println(MyClass.num);
    }
}
```

# Abstract class vs Interface

抽象类可以拥有抽象方法、非抽象方法和成员变量，而接口只能拥有抽象方法和常量。

一个类只能继承一个抽象类，但可以实现多个接口。

抽象类可以有构造函数，而接口不能有。

抽象类中，可以为成员应用访问修饰符（public、protected、private），而接口中所有成员默认为public

接口中的方法都是公共的并且没有方法体

# What is Method overloading and Method overriding?

