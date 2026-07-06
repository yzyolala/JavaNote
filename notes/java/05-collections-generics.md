# 集合框架、包装类与泛型

## Collection Framework

集合框架中的类和接口可以把一组对象表示为单个实体。集合大小是动态的，可以增加或减少元素。

## Collection 根接口

`Collection` 下常见子接口与实现：

- `List`
  - `ArrayList`
  - `LinkedList`
  - `Vector`
  - `Stack` 是 `Vector` 的子类
- `Set`
  - `HashSet`
  - `LinkedHashSet`
  - `TreeSet`
- `Queue`
  - `PriorityQueue`
  - `ArrayDeque`

## Collection 通用方法

| 方法 | 说明 |
| --- | --- |
| `isEmpty()` | 检查集合大小是否为 0 |
| `size()` | 返回集合大小 |
| `add(Object o)` | 添加对象 |
| `remove(Object o)` | 移除对象 |
| `clear()` | 移除所有对象 |
| `contains(Object o)` | 检查集合是否包含对象 |
| `toArray()` | 转为对象数组 |
| `iterator()` | 返回迭代器 |

## Arrays vs Collection

| 对比点 | Array | Collection |
| --- | --- | --- |
| 长度 | 固定 | 动态 |
| 存储类型 | 基本类型和对象类型 | 对象类型 |
| 访问方式 | 索引访问 | 迭代器或 foreach |
| 结构 | 可多维 | 多种接口与实现 |

## List vs Set

| 对比点 | List | Set |
| --- | --- | --- |
| 有序性 | 有序 | 通常无序，具体取决于实现 |
| 重复元素 | 允许重复 | 不允许重复 |
| 访问方式 | 可通过索引访问 | 通常通过迭代器访问 |
| 常见实现 | `ArrayList`、`LinkedList`、`Vector` | `HashSet`、`TreeSet`、`LinkedHashSet` |

## HashSet

- 基于哈希表数据结构实现。
- 插入对象时不保证保持原始插入顺序。
- 对象根据哈希码插入。
- 允许插入 `null` 元素。
- 使用 `hashCode()` 和 `equals()` 判断元素是否重复。

## LinkedHashSet

`LinkedHashSet` 与 `HashSet` 类似，但使用双向链表维护数据，因此可以保留元素插入顺序。

## TreeSet

- 使用树结构存储元素。
- 按自然排序或显式提供的比较器排序。
- 如果要正确实现 `Set` 语义，比较器应与 `equals()` 保持一致。
- 创建集合时可以通过构造函数传入比较器。
- 使用 `compareTo()` 或 `Comparator.compare()` 判断元素顺序和重复。

## HashSet vs TreeSet

| 对比点 | HashSet | TreeSet |
| --- | --- | --- |
| 内部实现 | 哈希表 | 红黑树 |
| 顺序 | 无序 | 有序 |
| 性能 | 插入、删除、查找通常更快 | 可有序遍历，但操作成本更高 |
| 判断重复 | `hashCode()` + `equals()` | `compareTo()` 或 `Comparator.compare()` |

## PriorityQueue

`PriorityQueue` 是 `Queue` 接口实现，用于存储按自然顺序或自定义比较器排序的元素。

## ArrayDeque

- 可调整大小的数组实现。
- 可以从队列两端添加或删除元素。
- 没有固定容量限制，会按需增长。

## 包装类

包装类用于将基本数据类型包装为对象。

| 基本类型 | 包装类 |
| --- | --- |
| `byte` | `Byte` |
| `short` | `Short` |
| `int` | `Integer` |
| `long` | `Long` |
| `float` | `Float` |
| `double` | `Double` |
| `boolean` | `Boolean` |
| `char` | `Character` |

常用方法：

- `parseXXX()`：将字符串转换为基本类型。
- `toString()`：将包装对象转换为字符串。
- `valueOf()`：将基本类型或字符串转换为包装类对象。
- `xxxValue()`：将包装类对象转换为对应基本类型，例如 `intValue()`、`byteValue()`。

## 泛型

泛型用于提供类型安全。

```java
ArrayList names = new ArrayList();          // 原生类型，不保证类型安全
ArrayList<String> names = new ArrayList<>(); // 只能存储 String
```

`String` 在这里是类型参数。使用泛型可以避免集合中混入不希望的类型。

## Thread 创建方式

Java 中常见创建线程方式：

1. 继承 `Thread` 类并重写 `run()` 方法，然后调用 `start()`。
2. 实现 `Runnable` 接口并实现 `run()` 方法，再把实例传给 `Thread`，最后调用 `start()`。

## Thread 生命周期

| 状态 | 说明 |
| --- | --- |
| New | 创建了 `Thread` 对象，还未启动 |
| Runnable | 调用 `start()` 后，等待调度或正在运行 |
| Running | 线程被 CPU 调度执行 `run()` 中的代码 |
| Blocked | 因 I/O、等待锁等原因暂停执行 |
| Terminated | `run()` 执行结束或异常终止 |

## `sleep` vs `yield` vs `join`

| 方法 | 说明 |
| --- | --- |
| `sleep()` | 当前线程暂停指定时间，不释放已经持有的锁 |
| `yield()` | 当前线程提示调度器让出 CPU，但不保证一定让出 |
| `join()` | 当前线程等待另一个线程执行结束后再继续 |
