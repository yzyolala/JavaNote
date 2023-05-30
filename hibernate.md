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

