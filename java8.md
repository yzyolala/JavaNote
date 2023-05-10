# java8

于2014年发布

最新版本为19，最新的LTS（长期支持）版本为17

Java 8是当前工业界广泛使用的版本

Java 8通过启用函数式编程帮助编写简洁的代码

Java 8新增功能包括：

● 函数式编程（编写简洁的代码）

● Lambda表达式

● 函数式接口

● 预定义的函数式接口：Predicate、Function、Supplier、Consumer

● 流

● 接口中的默认和静态方法

● :: 运算符

● Optional类

# Lambda表达式：

● 目的：实现函数式编程

● 它是一种方法/函数表示和匿名方法

● Lambda表达式是一种没有名称、修饰符和返回类型的方法表示形式

● 使用的特殊符号是 ->

# 函数式接口(Functional Interface)

指的是仅有一个抽象方法的接口

例如Runnable就是一个函数式接口，因为它只有一个抽象方法run()

我们可以使用注解@FunctionalInterface来明确声明一个接口为函数式接口

# 预定义函数式接口:Function、Predicate、Consumer和Supplier

这些接口都是在java.util.function包中定义的

Function接口

Function 接口表示一个接受一个参数并产生一个结果的函数。它定义了一个apply方法，该方法接受一个参数并返回一个结果。例如，我们可以使用Function将一个字符串转换为整数：

```java
Function<String, Integer> stringToInt = s -> Integer.parseInt(s);
int result = stringToInt.apply("123"); // result = 123
```

Predicate接口

Predicate 接口表示一个谓词，即一个返回布尔值的函数。它定义了一个test方法，该方法接受一个参数并返回一个布尔值。例如，我们可以使用Predicate检查一个字符串是否为空：

```java
Predicate<String> isEmpty = s -> s.isEmpty();
boolean result = isEmpty.test(""); // result = true
```
Consumer接口

Consumer 接口表示一个接受一个参数但不返回任何结果的函数。它定义了一个accept方法，该方法接受一个参数并执行一些操作。例如，我们可以使用Consumer打印一个字符串：

```java
Consumer<String> printString = s -> System.out.println(s);
printString.accept("Hello, world!"); // 输出：Hello, world!
```

Supplier接口

Supplier 接口表示一个不接受任何参数但返回一个结果的函数。它定义了一个get方法，该方法不接受任何参数但返回一个结果。例如，我们可以使用Supplier生成一个随机数：

```java
Supplier<Double> randomValue = () -> Math.random();
double result = randomValue.get(); // result = 0.123456789
```
# 流 Stream

● 用于将一组对象表示为单个实体

● Streams 用于处理集合中的对象

引入于 Java 8 的 Stream API 用于处理集合中的对象

一个流（Stream）是一系列对象的序列，支持各种方法，可以使用流水线式操作来生成所需的结果

● 我们可以使用各种方法在流上处理对象

流上的方法：

map: map 方法用于返回一个由将给定函数应用于此流的元素而生成的结果组成的流。Map 方法使用 Function 函数式接口。
List number = Arrays.asList(2,3,4,5);
List square = number.stream().map(x->x*x).collect(Collectors.toList());

filter: filter 方法用于根据传递的 Predicate 选择元素。Filter 总是需要 Predicate。
List names = Arrays.asList("Reflection","Collection","Stream");
List result = names.stream().filter(s->s.startsWith("S")).collect(Collectors.toList());

sorted: sorted 方法用于对流进行排序。这可以使用 lambda 表达式来比较对象。
List names = Arrays.asList("Reflection","Collection","Stream");
List result = names.stream().sorted().collect(Collectors.toList());

count: 返回流中对象的数量

forEach: 此方法需要 Consumer，并为每个对象执行此 Consumer

collect: 用于收集结果的方法

以下是一个简单的使用流的例子：

假设我们有一个整数列表，想要得到一个新的列表，其中每个元素都是原列表中的元素的平方，那么我们可以使用流和 map 方法来实现：

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> squares = numbers.stream()
                                .map(x -> x * x)
                                .collect(Collectors.toList());
System.out.println(squares); // 输出 [1, 4, 9, 16, 25]
```
这里，我们首先将一个整数列表转换成一个流，然后使用 map 方法将每个元素映射为它的平方，最后使用 collect 方法将结果收集到一个新的列表中。

另外，我们可以使用 filter 方法来筛选出符合特定条件的元素。例如，我们想要得到一个新的字符串列表，其中所有字符串都以字母 "a" 开头，那么可以使用流和 filter 方法来实现：

```java
List<String> names = Arrays.asList("apple", "banana", "orange", "avocado");
List<String> filteredNames = names.stream()
                                    .filter(s -> s.startsWith("a"))
                                    .collect(Collectors.toList());
System.out.println(filteredNames); // 输出 [apple, avocado]
```
这里，我们首先将一个字符串列表转换成一个流，然后使用 filter 方法筛选出以字母 "a" 开头的字符串，最后使用 collect 方法将结果收集到一个新的列表中。
