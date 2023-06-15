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

4.创建一个叫model的文件夹，在里面根据所需创建各种类文件

5.设置@Entity@Id@GeneratedValue(strategy = GenerationType.IDENTITY)@Getter

@Setter( @Getter@Setter 通过lombok可以直接getter&setter)

之所以需要getter&setter是因为类的属性基本都设定为private

6.然后根据数据库关系设定@OneToOne@OneToMany@ManyToMany

7.此时数据库功能基本实现，现在需要增删改查功能，这时候就要开始创建各种repository来实现了

8.创建一个叫repository的文件夹，在里面根据所需创建各种接口文件，不是类文件哦

9.基本格式：

```java
@Repository
public interface CustomerRepository extends CrudRepository<Customer,Long> {
}
```

10.然后在主的application文件就可以开始注入数据了，可以开始注入之前学过的repository文件了，基本格式如下：

```java
@SpringBootApplication
public class EcommBackendApplication implements CommandLineRunner {

    @Autowired
    private OrderRepository orderRepository;
    
    public static void main(String[] args) {
        SpringApplication.run(EcommBackendApplication.class, args);
    }

    @Override
    public void run(String... args) throws Exception {

        Order r= new Order();
        r.setStatus(OrderStatus.CREATED);
        r.setOrderAt(LocalDateTime.now());
        orderRepository.save(r);
    }
}

```

需要注意的是要：

a.implements CommandLineRunner

b.注入对应的repository
```java
@Autowired
  private OrderRepository orderRepository;
```

c.在Exception里面编写内容

d.写完新的对象这段代码：Order r= new Order(); 之后就要条件反射地写上orderRepository.save(r);

e.然后再给对象设置各种属性，这里因为之前倒入了lombok了，所以就会出现对应的set方法进行设置
