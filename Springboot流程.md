1.通过spring.io.start创建新的project(选择spring initializr)
2.需要的dependencies选择如下：
```java
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>com.mysql</groupId>
            <artifactId>mysql-connector-j</artifactId>
            <scope>runtime</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
            <dependency>
                <groupId>org.projectlombok</groupId>
                <artifactId>lombok</artifactId>
                <version>1.18.28</version>
                <scope>provided</scope>
            </dependency>
    </dependencies>
```
3.找到resources文件下的application.properties文件，输入以下代码来设置连接数据库数据：
```java
spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce?useSSL=false
spring.datasource.username=root
spring.datasource.password=12345678
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.show-sql=true
spring.jpa.hibernate.ddl-auto=create
```
4.根据所需创建各种类文件
5.设置@Entity@Id@GeneratedValue(strategy = GenerationType.IDENTITY)@Getter
@Setter( @Getter@Setter 通过lombok可以直接getter&setter)
6.之所以
