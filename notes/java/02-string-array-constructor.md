# 字符串、数组与构造方法

## String

- `String` 是不可变对象，一旦创建，内容不能被修改。
- 字符串使用双引号，字符使用单引号。

```java
String a = "hello";          // 字符串常量池
String b = new String("hi"); // 使用 new 在 heap 上创建对象
char c = 'a';
```

## String、StringBuffer、StringBuilder

| 类型 | 是否可变 | 是否线程安全 | 适合场景 |
| --- | --- | --- | --- |
| `String` | 不可变 | 是 | 字符串内容不频繁变化 |
| `StringBuffer` | 可变 | 是 | 多线程字符串拼接 |
| `StringBuilder` | 可变 | 否 | 单线程字符串拼接，速度更快 |

记忆：单线程拼接优先用 `StringBuilder`；多线程需要线程安全时用 `StringBuffer`。

## 数组

- 数组大小一旦创建就不能改变。
- 数组在连续内存中存储数据。
- 数组只能存储同一种类型的数据。
- 数组可以存储基本数据类型，也可以存储对象类型。
- 数组可以是多维数组。

```java
int[] arr = new int[2];
int[] marks = {10, 20, 30, 16};
```

## ArrayList 和数组

- 数组长度固定。
- `ArrayList` 是动态长度集合，大小可以增加或减少。

## 构造方法

构造方法是在对象被创建时调用的特殊方法。

规则：

- 构造方法名必须与类名完全相同。
- 可以有参数，也可以没有参数。
- 构造方法没有返回值。
- 如果没有定义构造方法，编译器会提供默认构造方法。

```java
class Student {
    String name;

    Student() {
    }

    Student(String name) {
        this.name = name;
    }
}
```

构造方法类型：

- **默认构造函数**：无参数，用默认值初始化成员变量。
- **带参数构造函数**：通过传入参数初始化成员变量。
