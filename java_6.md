# 集合框架
几个类和接口可以一起使用，将一组对象表示为单个实体。集合具有动态大小，意味着它们是可扩展的—我们可以增加或减少大小。

## 结构

### Collection根接口：

- List子接口：ArrayList实现类, LinkedList实现类, Vector实现类（Stack子类）
- Set子接口：HashSet实现类, LinkedHashSet实现类
- Queue子接口：PriorityQueue实现类, ArrayDeque实现类

### Map接口：

Map接口不是Collection接口的子接口。

## Collection通用方法：

- isEmpty() - 检查集合的大小是否为零
- size() - 给出集合的大小
- add(Object o) - 向集合中添加特定对象
- remove(Object o) - 移除集合中的特定对象
- clear() - 移除集合中的所有对象
- contains(Object o) - 检查集合是否包含给定对象
- toArray() - 给出对象数组
- iterator() - 返回Iterator对象，用于迭代集合中的对象

## HashSet：

- HashSet类基于哈希表数据结构实现
- 插入到HashSet中的对象不能保证以原有顺序插入
- 对象是根据它们的哈希码来插入的
- 允许插入NULL元素

## LinkedHashSet：

LinkedHashSet与HashSet非常相似，不同之处在于它使用双向链表来存储数据并保留元素的插入顺序。

## TreeSet：

- TreeSet使用树结构进行存储
- TreeSet通过自然排序或提供的显式比较器来维护元素的排序
- 如果要正确实现Set接口，则比较器必须与equals方法一致
- 根据使用哪个构造函数，也可以在创建集合时提供比较器进行排序

## PriorityQueue：

PriorityQueue是Queue接口的一个实现，用于存储按照自然顺序或者自定义比较器排序的元素。

## ArrayDeque：

- 提供了一种可调整大小的数组实现
- ArrayDeque是一种特殊类型的数组，允许从队列的两侧添加或删除元素
- 没有容量限制，会根据需要自动增长

## 包装类

包装类（如 `Integer`, `Double` 等）用于包装基本数据类型。包装类中的实用方法包括：

- parseXXX()方法：将字符串值转换为基本类型
- toString()方法：将包装对象转换为字符串
- valueOf()方法：将基本类型和字符串转换为包装类对象
- xxxValue()方法：将包装类对象转换为其对应的基本类型，如byteValue()、intValue()等

## 泛型：

- 泛型是为了提供类型安全，而原生集合（不使用泛型）是类型不安全的
- 集合可以存储多种类型的数据，但如果我们只想存储一种特定类型的数据，可以使用泛型来提供类型安全性
- 例如，`ArrayList names = new ArrayList();` 这个ArrayList可以存储任何类型的数据，不保证类型安全
- 而`ArrayList<String> names = new ArrayList<>();` 这个ArrayList是类型安全的，表示我们只能在这个ArrayList中存储字符串数据类型。这里的`String`被称为类型参数

  
