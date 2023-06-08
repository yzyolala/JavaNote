# @OneToOne(cascade = CascadeType.ALL)中**cascade = CascadeType.ALL**的注解:

当你对User对象执行持久化操作时（如保存），关联的Profile对象也会被同时保存。类似地，当你对User对象进行更新、删除等操作时，关联的Profile对象也会受到相同的操作影响

## @JoinTable(name = "student_course", joinColumns = @JoinColumn(name="student_id",referencedColumnName = "id"), inverseJoinColumns =@JoinColumn(name="course_id",referencedColumnName = "id"))

## @ManyToMany(mappedBy = "courses")


这段代码涉及到两组注解，让我逐一解释它们的含义和用法：

@JoinTable(name = "student_course", joinColumns = @JoinColumn(name="student_id",referencedColumnName = "id"), inverseJoinColumns =@JoinColumn(name="course_id",referencedColumnName = "id"))

这个注解用于定义多对多关系的关联表和关联列。
name = "student_course"指定了**关联表**的名称为"student_course"。
joinColumns = @JoinColumn(name="student_id",referencedColumnName = "id")表示在关联表中与学生实体相关的列。
name="student_id"指定了在关联表中表示学生ID的列的名称。
referencedColumnName = "id"指定了在学生实体表中表示主键ID的列的名称。
inverseJoinColumns =@JoinColumn(name="course_id",referencedColumnName = "id")表示在关联表中与课程实体相关的列。
name="course_id"指定了在关联表中表示课程ID的列的名称。
referencedColumnName = "id"指定了在课程实体表中表示主键ID的列的名称。
这些注解的目的是为了定义多对多关系的数据库映射。通过指定关联表的名称和关联列的名称，JPA可以自动创建关联表，并根据注解中的指定将相关列与实体的主键列进行关联。这样，就可以通过该关联表来跟踪学生和课程之间的多对多关系。

@ManyToMany(mappedBy = "courses")

这个注解用于指定另一个实体类中定义的多对多关系的反向映射。
mappedBy = "courses"中的"courses"指定了另一个实体类中表示该多对多关系的属性名。
这个注解的作用是告诉JPA，**该多对多关系由另一个实体类中的"courses"属性进行维护**，不需要在当前实体类中创建额外的关联表或关联列。
这两组注解一起使用可以实现多对多关系的映射。通过第一组注解，定义了关联表和关联列，而第二组注解指定了反向映射，使得多对多关系能够在两个实体类之间进行双向的访问和操作。

## @GeneratedValue(strategy = GenerationType.IDENTITY)@GeneratedValue(strategy = GenerationType.AUTO)怎么使用 有什么区别

GenerationType.AUTO:把主键生成策略交给持久化引擎,此种主键生成策略比较常用,由于JPA默认的生成策略就是GenerationType.AUTO,所以使用此种策略时.可以显式的指定@GeneratedValue(strategy = GenerationType.AUTO)也可以直接@GeneratedValue

GenerationType.IDENTITY：该策略通常适用于使用自增列（如MySQL中的AUTO_INCREMENT）来生成主键的数据库。当使用IDENTITY策略时，数据库将负责生成唯一的主键值，并在插入数据时立即分配主键。在这种情况下，可以使用@GeneratedValue(strategy = GenerationType.IDENTITY)来指定主键的自动生成策略，**重点：选择自增长策略后，创建setter方法或constructor不能涵盖该参数**

referencedColumnName = "id"指定了在学生实体表中表示主键ID的列的名称。

# #@OneToMany使用套路

主表的属性通常搭配@OneToMany加上对应另一个表属性的Set集合 例如：
```java
@OneToMany(mappedBy = "student")
Set<Vehicle> vehicles = new HashSet<>();
```

副表属性通常搭配@ManyToOne来被对应，再加上一个@JoinColumn标签来规定额外的关系表，定义该关系表的表名字（name=""），内部再用referencedColumnName来规定被跟随的主表属性是哪个

```java
@ManyToOne
@JoinColumn(name="s_id",referencedColumnName = "id")
    Student student;
```
