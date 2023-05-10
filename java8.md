1.函数式接口:Function、Predicate、Consumer和Supplier

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
