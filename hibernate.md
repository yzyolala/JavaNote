# 介绍

它是一个ORM工具（对象关系映射）。

实现了JPA（Java持久化API），它是一组接口的标准。

Hibernate由一些类组成，为JPA中的接口提供了具体的实现。

为什么选择Hibernate？它提供了支持Java程序连接到数据库的功能，它简化了与数据库的交互。

Java Program < ------------------> ORM(Hibernate) < ------------------------> Database

# 创建步骤

1.创建一个maven项目

2.添加依赖

```java
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>org.example</groupId>
  <artifactId>TestHN</artifactId>
  <version>1.0-SNAPSHOT</version>
  <packaging>jar</packaging>

  <name>TestHN</name>
  <url>http://maven.apache.org</url>

  <properties>
    <maven.compiler.target>1.8</maven.compiler.target>
    <maven.compiler.source>1.8</maven.compiler.source>
  </properties>

  <dependencies>

    <dependency>
      <groupId>org.hibernate</groupId>
      <artifactId>hibernate-core</artifactId>
      <version>6.1.2.Final</version>
    </dependency>

    <dependency>
      <groupId>mysql</groupId>
      <artifactId>mysql-connector-java</artifactId>
      <version>8.0.28</version>
    </dependency>
  </dependencies>
</project>
```

3.添加配置文件

创建一个hibernate.cfg.xml的文件，并把它放在名为resources的文件下（不能拼错），resources文件要与java文件同级别

```java
<?xml version = "1.0" encoding = "utf-8"?>
<!DOCTYPE hibernate-configuration SYSTEM "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
    <session-factory>
        <property name = "hibernate.connection.driver_class">com.mysql.cj.jdbc.Driver</property>
        <property name = "hibernate.connection.url">jdbc:mysql://localhost:3306/university?useSSL=false</property>//这一行修改university为数据库的库名字
        <property name = "hibernate.connection.username">root</property>
        <property name = "hibernate.connection.password">12345678</property>
        <property name = "hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>
        <property name="hibernate.hbm2ddl.auto">update</property>//update意思是注入数据时不删除之前数据，直接添加；若是每次都初始化数据应该用create
        <property name="show_sql">true</property>
        <mapping class ="org.example.Customer"/>//类名，有几个类就添加几个
        <mapping class="org.example.OrderItem"/>
    </session-factory>
</hibernate-configuration>
```
4.在java下创建类文件，用app文件执行

# 注释用法

@Entity - Used to tell hibernate to treat class as table in database

@Id - Declare a class member variable as primary key of the table（必须有）

@Table(name = “”) - Configure the name of table

@Column(name = “”) - Configure the name of column

@GeneratedValue(strategy = GenerationType.IDENTITY) - Generate values for the primary key column 用于指定主键的生成策略，例如自增长、UUID、序列等

@OneToMany: 一对多

@ManyToOne: 多对一

@ManyToMany: 多对多

@JoinColumn: 用于指定关联实体对象在数据库中的外键列

# 注意事项

@GeneratedValue自增长注释的属性不能放在constructor中，因为已经自增长不需要定义

类文件 最后要额外需要写一个public Customer(){}的无参构造

# App执行类注意事项

```java
public class App
{
    public static void main( String[] args )
    {
        OrderItem or1= new OrderItem(2,"Apple");
        OrderItem or2= new OrderItem(3,"Chicken");

        Set<OrderItem> set= new HashSet<>();

        set.add(or1);
        set.add(or2);

        Customer c= new Customer("Jerry",set);

        or1.setCustomer(c);
        or2.setCustomer(c);

        SessionFactory factory = new Configuration().configure().buildSessionFactory();
        Session session = factory.openSession();
        Transaction t = session.beginTransaction();

        session.persist(or1);
        session.persist(or2);
        session.persist(c);
        t.commit();
        session.close();

    }
}
```



