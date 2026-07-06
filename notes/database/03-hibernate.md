# Hibernate

## 介绍

Hibernate 是一个 ORM 工具，即对象关系映射工具。

它实现了 JPA（Java Persistence API）规范。JPA 是一组接口标准，Hibernate 提供这些接口的具体实现。

```text
Java Program <----> ORM (Hibernate) <----> Database
```

为什么选择 Hibernate：

- 支持 Java 程序连接数据库。
- 简化 Java 与数据库交互。
- 让开发者以对象方式操作数据库。

## 创建步骤

### 1. 创建 Maven 项目

先创建 Maven 项目。

### 2. 添加依赖

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
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

### 3. 添加配置文件

创建 `hibernate.cfg.xml`，放在 `resources` 文件夹下。`resources` 需要与 `java` 文件夹同级，名字不能拼错。

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE hibernate-configuration SYSTEM "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
    <session-factory>
        <property name="hibernate.connection.driver_class">com.mysql.cj.jdbc.Driver</property>
        <property name="hibernate.connection.url">jdbc:mysql://localhost:3306/university?useSSL=false</property>
        <property name="hibernate.connection.username">root</property>
        <property name="hibernate.connection.password">12345678</property>
        <property name="hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>
        <property name="hibernate.hbm2ddl.auto">update</property>
        <property name="show_sql">true</property>
        <mapping class="org.example.Customer" />
        <mapping class="org.example.OrderItem" />
    </session-factory>
</hibernate-configuration>
```

注意：

- `university` 替换为实际数据库名。
- `hibernate.hbm2ddl.auto=update` 表示注入数据时不删除原数据，直接更新/添加。
- 如果希望每次初始化数据，可使用 `create`。
- 有几个实体类，就添加几个 `<mapping class="..." />`。

### 4. 创建类文件和 App 执行类

在 `java` 下创建实体类，用 App 类执行。

## 常用注解

| 注解 | 说明 |
| --- | --- |
| `@Entity` | 告诉 Hibernate 将该类当作数据库表处理 |
| `@Id` | 声明成员变量为表的主键，必须有 |
| `@Table(name = "")` | 配置表名 |
| `@Column(name = "")` | 配置列名 |
| `@GeneratedValue(strategy = GenerationType.IDENTITY)` | 指定主键生成策略，例如自增长、UUID、序列等 |
| `@OneToMany` | 一对多 |
| `@ManyToOne` | 多对一 |
| `@ManyToMany` | 多对多 |
| `@JoinColumn` | 指定关联实体对象在数据库中的外键列 |

## 注意事项

- 使用 `@GeneratedValue` 自增长后，不要在 constructor 中设置该主键属性。
- 实体类需要额外提供无参构造方法，例如 `public Customer() {}`。

## App 执行类示例

```java
public class App {
    public static void main(String[] args) {
        OrderItem or1 = new OrderItem(2, "Apple");
        OrderItem or2 = new OrderItem(3, "Chicken");

        Set<OrderItem> set = new HashSet<>();
        set.add(or1);
        set.add(or2);

        Customer c = new Customer("Jerry", set);

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

关键流程：

1. 创建 `SessionFactory`。
2. 打开 `Session`。
3. 开启事务。
4. `persist()` 持久化对象。
5. `commit()` 提交事务。
6. 关闭 `Session`。
