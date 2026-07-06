# Java 8、Lambda 与 Stream

## Java 8 概览

- Java 8 发布于 2014 年。
- Java 8 是工业界长期广泛使用的版本之一。
- Java 8 引入函数式编程能力，使代码更简洁。
- 原笔记中提到：最新版本为 19，最新 LTS 为 17。

## Java 8 主要特点

- 函数式编程
- Lambda 表达式
- 函数式接口
- 预定义函数式接口：`Predicate`、`Function`、`Supplier`、`Consumer`
- Stream API
- 接口中的默认方法和静态方法
- `::` 方法引用运算符
- `Optional` 类

## Lambda 表达式

Lambda 表达式是方法或函数的匿名表示形式。

特点：

- 支持函数式编程。
- 没有名称、修饰符和显式返回类型。
- 使用 `->` 作为特殊符号。

```java
(x, y) -> x + y
```

## 函数式接口

函数式接口是只有一个抽象方法的接口。

例如，`Runnable` 是函数式接口，因为它只有一个抽象方法 `run()`。

可以使用 `@FunctionalInterface` 注解明确声明：

```java
@FunctionalInterface
interface MyTask {
    void run();
}
```

## 预定义函数式接口

这些接口定义在 `java.util.function` 包中。

### Function

`Function<T, R>` 表示接受一个参数并产生一个结果的函数，核心方法是 `apply()`。

```java
Function<String, Integer> stringToInt = s -> Integer.parseInt(s);
int result = stringToInt.apply("123"); // 123
```

### Predicate

`Predicate<T>` 表示返回布尔值的函数，核心方法是 `test()`。

```java
Predicate<String> isEmpty = s -> s.isEmpty();
boolean result = isEmpty.test(""); // true
```

### Consumer

`Consumer<T>` 表示接受一个参数但不返回结果的函数，核心方法是 `accept()`。

```java
Consumer<String> printString = s -> System.out.println(s);
printString.accept("Hello, world!");
```

### Supplier

`Supplier<T>` 表示不接受参数但返回结果的函数，核心方法是 `get()`。

```java
Supplier<Double> randomValue = () -> Math.random();
double result = randomValue.get();
```

## Stream

Stream API 引入于 Java 8，用于处理集合中的对象。

Stream 是一系列对象的序列，支持流水线式操作以生成结果。

常见方法：

| 方法 | 说明 | 函数式接口 |
| --- | --- | --- |
| `map()` | 对每个元素执行转换，返回转换后的流 | `Function` |
| `filter()` | 根据条件筛选元素 | `Predicate` |
| `sorted()` | 对流排序 | 可搭配 lambda / Comparator |
| `count()` | 返回流中元素数量 | - |
| `forEach()` | 对每个元素执行操作 | `Consumer` |
| `collect()` | 收集流处理结果 | - |

### map 示例

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> squares = numbers.stream()
    .map(x -> x * x)
    .collect(Collectors.toList());

System.out.println(squares); // [1, 4, 9, 16, 25]
```

### filter 示例

```java
List<String> names = Arrays.asList("apple", "banana", "orange", "avocado");
List<String> filteredNames = names.stream()
    .filter(s -> s.startsWith("a"))
    .collect(Collectors.toList());

System.out.println(filteredNames); // [apple, avocado]
```

### sorted 示例

```java
List<String> names = Arrays.asList("Reflection", "Collection", "Stream");
List<String> result = names.stream()
    .sorted()
    .collect(Collectors.toList());
```
