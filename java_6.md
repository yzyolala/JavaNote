# 集合框架
几个类和接口可以一起使用来将一组对象表示为单个实体
动态大小-集合是可扩展的-我们可以增加或减少大小

# 结构

Collection根接口：

List子接口：ArrayList实现类,LinkedList实现类,Vector实现类（Stack子类）

Set子接口：HashSet实现类,LinkedHashSet实现类

Queue子接口：PriorityQueue实现类, ArrayDeque实现类

Map接口：不是Collection接口的子接口

# Collection包含所有集合类通用方法：

isEmpty() - 检查集合的大小是否为零 

size() - 给出集合的大小 

add(Object o) - 向集合中添加特定对象  

remove(Object o) - 移除集合中的特定对象 

clear() - 移除集合中的所有对象  

contains(Object o) - 检查集合是否包含给定对象

toArray() - 给出对象数组 iterator() - 返回Iterator对象，用于迭代集合中的对象

# HashSet：

HashSet类是哈希表数据结构的内在实现

我们插入到HashSet中的对象不能保证顺序插入

对象是根据它们的哈希码插入的

允许插入NULL元素

# LinkedHashSet：

LinkedHashSet与HashSet非常相似，不同之处在于它使用双向链表来存储数据并保留元素的顺序

# TreeSet：

TreeSet类使用树进行存储

使用自然排序的set通过比较器或提供的显式比较器维护元素的排

如果要正确实现Set接口，则比较器必须与equals一致

它也可以通过在集合创建时提供比较器来排序，这取决于使用哪个构造函数

# Priority Queue：

当对象需要根据优先级进行处理时，就可以使用优先队列

队列通常遵循先进先出（FIFO）算法，但有时需要根据优先级处理队列中的元素，这时就可以使用这个类

# ArrayDeque：

提供了一种可调整大小的数组方式

它是一种特殊类型的数组，可以增长并允许用户从队列的两侧添加或删除元素

Array deque没有容量限制，它会根据需要增长以支持使用

#包装类

包装类中的实用方法：

parseXXX()方法将字符串值转换为基本类型

toString()方法将包装对象转换为字符串

valueOf()方法将基本类型和字符串转换为包装类对

xxxValue()方法将包装类转换为基本类型，如byteValue()、intValue()等

# 泛型：

泛型是为了提供类型安全，collection是不安全的

集合可以存储多种类型的数据，但是如果我们只想存储一种特定类型的数据，我们可以使用泛型来为集合提供类型安全性

例如，ArrayList names = new ArrayList()；这个ArrayList可以存储任何类型的数据，不保证类型安全

而ArrayList<String> names = new ArrayList<String>()；这个ArrayList是类型安全的，表示我们只能在这个ArrayList中存储字符串数据类型
  
ArrayList<String> names = new ArrayList<String>()；这里的String被称为类型参数
  
