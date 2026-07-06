# Java 基础

## 为什么 Java 受欢迎

- **平台无关性**：Java 程序编译为字节码后，可以在安装了 JVM 的不同操作系统和硬件平台上运行。
- **面向对象编程**：Java 使用对象组织代码，便于复用、维护和扩展。
- **丰富的库和框架**：Java 生态中有大量库和框架，覆盖数据库、Web、网络、GUI 等场景。
- **安全性**：Java 具有内置安全机制，可控制资源访问，适合 Web 应用开发。
- **社区支持**：Java 拥有成熟活跃的开发者社区和长期维护的框架生态。

## JDK、JRE、JVM

JDK = JRE + `javac` 编译器 + 开发工具。JRE = JVM + 类库。

| 项目 | JDK | JRE | JVM |
| --- | --- | --- | --- |
| 基本定义 | Java 开发工具包 | Java 运行环境 | 执行字节码的虚拟机 |
| 组成 | JRE、`javac`、开发工具 | JVM、libraries | 包含在 JDK/JRE 中 |
| 主要功能 | 开发、编译、调试 Java 程序 | 运行 Java 程序 | 执行 `.class` 字节码 |
| 是否包含 `javac` | 是 | 否 | 否 |

## 基本概念

- **Identifier**：Java 程序中的名字，例如类名、方法名、变量名等。
- **1 byte = 8 bits**。
- Java 程序可以有多个类，但一个源文件中最多只能有一个 `public` 类，且文件名必须与 `public` 类名一致。
- 每个 Java 类都会生成一个 `.class` 文件。
- 每个 Java 程序只能有一个真正作为入口使用的 `main` 方法。

## Source File Structure

一个 `.java` 文件通常包含：

1. `package` statement：最多 1 个。
2. `import` statements：可以有任意多个。
3. `class` / `interface` / `enum` 定义。

导入方式：

```java
import java.util.Scanner; // 显式导入
import java.util.*;       // 通配符导入
```

## 类和对象

- **Class**：类是创建对象的蓝图或模板，包含变量和方法。
- **Object**：对象是类的实例，是运行时真实占用内存的实体。

```java
class Student {
    String name;
    int age;

    void study() {
        System.out.println(name + " is studying");
    }
}
```

## 方法语法

```java
accessModifier returnType methodName(dataType variable) {
    // code
    return value;
}
```

## 数据类型

Java 有 8 种原始数据类型：

- `byte`
- `short`
- `int`
- `long`
- `float`
- `double`
- `char`
- `boolean`

按常见占用空间排序：

```text
double(8 bytes) = long(8 bytes)
> float(4 bytes) = int(4 bytes)
> short(2 bytes) = char(2 bytes)
> byte(1 byte)
> boolean(usually 1 byte)
```

常用选择：

- 小数一般用 `double`。
- 整数一般用 `int`。

## 类型转换

- 小类型转大类型：自动转换。
- 大类型转小类型：需要强制类型转换。

```java
int a = 10;
double b = a;      // 自动转换
int c = (int) b;   // 强制转换
```

## `this` vs `super`

- `this`：引用当前对象，用于访问当前对象的实例变量或方法，也常用于解决变量名冲突。
- `super`：引用父类对象，用于访问父类的构造函数、变量或方法。

## `static` 和静态代码块

- `static` 成员属于类级别，可以不创建对象，直接通过类名访问。
- 静态代码块用于初始化静态成员变量，只在类加载时执行一次，并且早于普通对象创建。

```java
public class Example {
    public static int staticVariable;

    static {
        System.out.println("静态代码块被执行");
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

## Enum

Java 枚举是一种特殊的类，通常用于表示固定常量集合，例如季节、月份、星期、方向等。

```java
enum Direction {
    EAST, SOUTH, WEST, NORTH
}
```

枚举可以提高代码可读性、可维护性和安全性。
