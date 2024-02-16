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

重载是在一个类里面，方法名字必须相同，而参数或参数列表必须不同，返回类型和访问修饰符可以相同也可以不同

方法能够在同一个类中或者在一个子类中被重载

重写不能对方法名、参数列表和返回值类型进行修改，访问修饰符不能比父类更严格（父类的一个方法被声明为 public，那么在子类中重写该方法就不能声明为 protected）

关键字 static、final 和 private 都不能被重写

| 特征             | 重载（Overload）                               | 重写（Override）                               |
|----------------|--------------------------------------------|--------------------------------------------|
| 定义位置          | 同一个类中或者子类中                             | 子类中                                       |
| 方法名           | 必须相同                                      | 必须相同                                      |
| 参数列表          | 必须不同                                      | 不能修改                                      |
| 返回类型          | 可以相同也可以不同                                | 不能修改                                      |
| 访问修饰符         | 可以相同也可以不同                                | 不能比父类更严格                                |
| 关键字 static、final 和 private | 可以被重载                                    | 不能被重写                                    |

# Why is multiple inheritance through classes not possible in Java?

名称冲突：如果多个父类中有相同的方法或变量，那么在子类中使用这些方法或变量时就会产生歧义。例如，如果父类A和父类B都有一个名为foo()的方法，而子类C继承了这两个父类，那么在C类中使用foo()方法时就无法确定调用哪个父类的foo()方法。

菱形继承问题：如果多个父类共同继承自同一个父类，那么子类在继承这些父类的同时也会继承这些父类中的公共父类。这样就会产生一个问题，就是当子类调用一个在公共父类中定义的方法时，它不知道该调用哪一个父类的实现。这被称为菱形继承问题，因为继承关系图形状像一个菱形。

# Difference between C c = new C() and P p = new C()

P p = new C()表示创建一个C类的对象。由于C类是P类的子类，因此该对象同样也是P类的一个实例。然而，由于p的类型是P，因此只能调用P类中定义的方法和访问P类中定义的属性，即使这个对象实际上是C类的一个实例。如果C类重写了P类中的方法，则会调用C类中的方法。

# Checked Exception vs Unchecked Exception

Checked exceptions指的是那些可以在编译时检测到并且需要在方法签名中声明的异常，以便在调用方法时处理。Checked exceptions通常表示程序中的预期情况。

Unchecked exceptions（如算术异常）指的是那些无法在编译时检测到的异常，通常是由程序逻辑错误引起的。这些异常在方法签名中不需要声明。

# What is Enum?

Java 枚举是一个特殊的类，一般表示一组常量，比如一年的 4 个季节，一个年的 12 个月份，一个星期的 7 天，方向有东南西北等。

Java 枚举类使用 enum 关键字来定义，各个常量使用逗号 , 来分割。它们可以提高代码的可读性，可维护性和安全性。

# Arrays vs Collection

数组是一个固定长度的数据结构，它可以存储基本数据类型和对象类型的元素。在创建数组时，必须指定它的长度，并且该长度在整个程序运行期间都不会改变。数组具有以下特点：

数组元素可以通过索引访问，索引从0开始。

数组可以存储基本数据类型和对象类型的元素。

数组长度是固定的，一旦创建就不能改变。

数组可以是多维的，也就是数组的元素可以是数组

集合是一个动态长度的数据结构，它可以存储对象类型的元素。在创建集合时，不需要指定其长度，集合会自动根据元素的数量来调整其大小。

Java中提供了多种类型的集合，如List、Set、Queue和Map等。集合具有以下特点：

集合元素可以通过迭代器或者foreach循环访问。

集合只能存储对象类型的元素。

集合的长度可以动态改变，根据元素的数量来自动调整。

集合可以实现多种接口，如List接口可以按照元素的插入顺序来保存元素，Set接口可以确保元素的唯一性。

# Difference between List and Set?

List和Set都是Java中的集合框架。它们在以下方面有所不同：

1.有序性：List是有序的集合，Set是无序的集合。

2.可重复性：List允许存储重复的元素，而Set不允许存储重复的元素。

3.访问方式：List可以通过索引进行访问。Set只能通过迭代器进行访问。

4.实现方式：List的实现包括ArrayList、LinkedList和Vector等。Set的实现包括HashSet、TreeSet和LinkedHashSet等。

# What is a Wrapper class?

包装类是用于将原始类型数据转换为对象的类，这使得它们可以拥有一些有用的方法。

Byte、Short、Integer、Long、Float、Double、Boolean、Character 是Java中的包装类。

它们具有以下方法：

● parseXXX()：将字符串值转换为相应的原始类型值

● toString()：将包装对象转换为字符串

● valueOf()：将原始类型和字符串转换为包装类对象

● xxxValue()：byteValue()、intValue() 等将包装类转换为相应的原始类型

# Difference between HashSet and TreeSet

HashSet和TreeSet都是的Set接口的实现类，它们之间有以下区别：

内部实现：HashSet使用哈希表实现，而TreeSet使用红黑树实现。

有序性：HashSet是无序的，而TreeSet是有序的。TreeSet可以按照元素的自然排序或者指定的比较器进行排序。

性能：由于HashSet使用哈希表，它在插入、删除和查找元素时的性能比TreeSet更高效。但是，TreeSet可以提供有序遍历集合的功能。

元素唯一性：HashSet通过hashCode()和equals()方法来判断元素是否重复，而TreeSet通过compareTo()或Comparator接口的compare()方法来判断元素是否重复

# In how many ways a Thread can be created?

1.继承Thread类并覆盖其run()方法：

创建一个继承自Thread类的子类，覆盖run()方法并在该方法中定义线程的主要逻辑。然后创建该类的对象，并调用start()方法启动线程。

2.实现Runnable接口：

创建一个实现Runnable接口的类，并实现该接口的run()方法。然后创建Thread类的对象并将该实现了Runnable接口的类的实例传递给Thread类的构造函数中，最后调用start()方法启动线程。

# Different Life cycles of Thread?

在Java中，线程的生命周期可以分为以下五个状态：

1.新建状态（New）：当一个Thread对象被创建时，它处于新建状态。

2.就绪状态（Runnable）：当线程被创建后，调用start()方法之前，线程处于就绪状态。此时，线程已经准备好运行，只需要等待系统调度它即可。

3.运行状态（Running）：当线程被系统调度时，进入运行状态。此时，线程正在执行run()方法中的代码。

4.阻塞状态（Blocked）：当线程在执行过程中，由于某些原因（如等待I/O操作、等待获取锁等），暂时停止了执行，此时进入阻塞状态。当阻塞的原因消除后，线程又会进入就绪状态。

5.终止状态（Terminated）：当线程执行完了run()方法中的代码或者抛出了异常而终止时，线程进入终止状态。

# sleep vs yield vs join

# What is Lambda expression and Functional Interface
# What are streams? explain few methods on streams
