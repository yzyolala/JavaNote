# Java Midterm Review

这份复习笔记汇总 Java 基础、OOP、异常、集合、线程和 Java 8 高频问答。

## Java 为什么受欢迎

- **平台无关性**：Java 可在安装 JVM 的不同系统和硬件平台运行。
- **面向对象**：代码以对象组织，更易复用、管理和扩展。
- **丰富库和框架**：生态覆盖数据库、GUI、网络、Web 等场景。
- **安全性**：Java 有内置安全机制，可控制资源访问。
- **社区支持**：社区活跃、资料多、框架成熟。

## Class 和 Object

- **Class**：类是创建对象的蓝图或模板，定义属性和方法。
- **Object**：对象是类的实例，是运行时实体，具有自己的属性值和行为。

## Java 源文件是否可以有多个类和多个 main 方法

- 一个 Java 源文件可以有多个类。
- 最多只能有一个 `public` 类，并且 `public` 类名必须与文件名相同。
- 每个 Java 程序入口通常只能有一个 `main` 方法。
- 如果源文件中定义多个同签名 `main` 方法，会产生编译错误。

## OOP Concepts

| 概念 | 说明 |
| --- | --- |
| Abstraction | 隐藏复杂实现，只暴露必要信息 |
| Encapsulation | 将数据和操作数据的方法封装在类中 |
| Inheritance | 子类通过 `extends` 继承父类属性和行为 |
| Polymorphism | 通过方法重载和方法重写实现多态 |

## String、StringBuffer、StringBuilder

| 类型 | 特点 | 场景 |
| --- | --- | --- |
| `String` | 不可变 | 字符串不经常改变 |
| `StringBuffer` | 可变、线程安全 | 多线程字符串修改 |
| `StringBuilder` | 可变、非线程安全、速度更快 | 单线程字符串修改 |

## Constructor

构造函数是创建对象时调用的特殊方法，与类名相同，没有返回类型。

类型：

- 默认构造函数：无参数，使用默认值初始化数据成员。
- 带参数构造函数：接收参数并用传入值初始化数据成员。

## `this` vs `super`

- `this` 引用当前对象，常用于访问当前对象变量/方法，避免变量名冲突。
- `super` 引用父类对象，常用于访问父类构造函数或方法。

## 访问修饰符

| 修饰符 | 访问范围 |
| --- | --- |
| `public` | 任何地方 |
| `protected` | 包内 + 外部包子类 |
| default | 当前包内 |
| `private` | 当前类内 |

顺序：`public` > `protected` > default > `private`。

## final、finally、finalize

- `final`：修饰类、方法、变量。类不可继承，方法不可重写，变量不可修改。
- `finally`：无论是否发生异常都会执行，常用于释放资源。
- `finalize`：对象销毁前可能由垃圾回收器调用，应谨慎使用。

## static 和 static block

- `static` 成员属于类，不需要实例化对象即可通过类名访问。
- 静态代码块在类加载时执行一次，用于初始化静态变量，早于主方法执行。

```java
public class Example {
    public static int staticVariable;

    static {
        staticVariable = 10;
    }

    public static void staticMethod() {
        System.out.println("静态方法被调用");
    }

    public static void main(String[] args) {
        System.out.println(Example.staticVariable);
        Example.staticMethod();
    }
}
```

## Abstract Class vs Interface

| 对比 | Abstract Class | Interface |
| --- | --- | --- |
| 方法 | 可有抽象方法和非抽象方法 | 主要定义行为，方法默认 public |
| 变量 | 可有成员变量 | 常量 |
| 继承数量 | 一个类只能继承一个抽象类 | 一个类可实现多个接口 |
| 构造函数 | 可以有 | 不能有 |
| 访问修饰符 | 可使用 public/protected/private | 成员默认 public |

## Method Overloading vs Overriding

| 对比 | Overloading | Overriding |
| --- | --- | --- |
| 位置 | 同类或子类 | 子类 |
| 方法名 | 相同 | 相同 |
| 参数列表 | 必须不同 | 必须相同 |
| 返回类型 | 可以相同或不同 | 必须兼容父类方法 |
| 访问修饰符 | 可以不同 | 不能比父类更严格 |
| static/final/private | 可重载 | 不能重写 |

## 为什么 Java 不支持类的多重继承

- 多个父类有同名方法或变量时会产生名称冲突。
- 多个父类继承同一祖先类时会出现菱形继承问题，子类无法确定使用哪个实现。

## `C c = new C()` vs `P p = new C()`

如果 `C` 是 `P` 的子类：

- `C c = new C()`：引用类型为 `C`，可调用 `C` 自己的方法。
- `P p = new C()`：引用类型为 `P`，只能调用 `P` 中定义的方法；如果 `C` 重写了方法，运行时执行 `C` 的实现。

## Checked Exception vs Unchecked Exception

- **Checked Exception**：编译时可检测，需要声明或处理，通常表示预期情况。
- **Unchecked Exception**：编译时不强制检测，通常由程序逻辑错误引起。

## Enum

枚举是特殊类，用于表示固定常量集合，例如季节、月份、星期、方向等。使用 `enum` 定义，常量用逗号分隔。

## Arrays vs Collection

| 对比 | Array | Collection |
| --- | --- | --- |
| 长度 | 固定 | 动态 |
| 存储类型 | 基本类型和对象类型 | 对象类型 |
| 访问方式 | 索引访问 | 迭代器或 foreach |
| 重复/顺序 | 取决于数组内容 | 取决于具体接口和实现 |

## List vs Set

| 对比 | List | Set |
| --- | --- | --- |
| 顺序 | 有序 | 通常无序 |
| 重复 | 允许重复 | 不允许重复 |
| 访问 | 可按索引访问 | 通常通过迭代器访问 |
| 实现 | `ArrayList`、`LinkedList`、`Vector` | `HashSet`、`TreeSet`、`LinkedHashSet` |

## Wrapper Class

包装类用于将原始类型转换为对象：

- `Byte`
- `Short`
- `Integer`
- `Long`
- `Float`
- `Double`
- `Boolean`
- `Character`

常用方法：

- `parseXXX()`
- `toString()`
- `valueOf()`
- `xxxValue()`

## HashSet vs TreeSet

| 对比 | HashSet | TreeSet |
| --- | --- | --- |
| 实现 | 哈希表 | 红黑树 |
| 顺序 | 无序 | 有序 |
| 性能 | 插入、删除、查找通常更快 | 支持有序遍历 |
| 重复判断 | `hashCode()` + `equals()` | `compareTo()` / `Comparator.compare()` |

## Thread 创建方式

1. 继承 `Thread` 类并重写 `run()` 方法。
2. 实现 `Runnable` 接口并实现 `run()` 方法，再传给 `Thread`。

两种方式最终都通过 `start()` 启动线程。

## Thread 生命周期

| 状态 | 说明 |
| --- | --- |
| New | 创建线程对象 |
| Runnable | 调用 `start()` 后等待调度或正在运行 |
| Running | CPU 正在执行线程代码 |
| Blocked | 因 I/O、锁等原因阻塞 |
| Terminated | 执行结束或异常终止 |

## `sleep` vs `yield` vs `join`

| 方法 | 说明 |
| --- | --- |
| `sleep()` | 当前线程暂停指定时间 |
| `yield()` | 当前线程提示调度器让出 CPU，但不保证生效 |
| `join()` | 等待另一个线程执行结束 |

## Lambda Expression 和 Functional Interface

- Lambda 是匿名函数表示形式，使用 `->`。
- Functional Interface 是只有一个抽象方法的接口，可用 Lambda 实现。

## Stream

Stream 用于处理集合对象，支持链式流水线操作。

常见方法：

- `map()`：转换元素。
- `filter()`：筛选元素。
- `sorted()`：排序。
- `count()`：统计数量。
- `forEach()`：逐个处理。
- `collect()`：收集结果。
