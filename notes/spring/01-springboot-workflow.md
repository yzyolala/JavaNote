# Spring Boot 项目流程

## 1. 创建项目

通过 [spring.io/start](https://spring.io/start) 创建新项目，选择 Spring Initializr。

## 2. 选择 Dependencies

常用依赖：

```xml
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

## 3. 配置数据库连接

在 `resources/application.properties` 中配置：

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce?useSSL=false
spring.datasource.username=root
spring.datasource.password=12345678
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.show-sql=true
spring.jpa.hibernate.ddl-auto=create
```

## 4. 创建 model 包

创建 `model` 文件夹，根据需求创建实体类。

常用注解：

```java
@Entity
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
@Getter
@Setter
```

`@Getter` 和 `@Setter` 来自 Lombok，可以自动生成 getter/setter。

为什么需要 getter/setter：实体类属性通常设置为 `private`。

## 5. 设置表关系

根据数据库关系设置：

- `@OneToOne`
- `@OneToMany`
- `@ManyToMany`

## 6. 创建 repository 包

创建 `repository` 文件夹，根据实体创建接口文件。注意是接口，不是类。

```java
@Repository
public interface CustomerRepository extends CrudRepository<Customer, Long> {
}
```

Repository 用于提供增删改查能力。

## 7. 在主 Application 中注入数据

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
        Order r = new Order();
        r.setStatus(OrderStatus.CREATED);
        r.setOrderAt(LocalDateTime.now());
        orderRepository.save(r);
    }
}
```

注意：

1. 主类实现 `CommandLineRunner`。
2. 使用 `@Autowired` 注入对应 repository。
3. 在 `run(String... args) throws Exception` 中编写初始化逻辑。
4. 创建对象后记得调用 `repository.save(object)`。
5. 因为引入 Lombok，可以直接使用对应的 setter 方法设置属性。

## 8. 创建 controller 包

创建 `controller` 文件夹，并创建例如 `ProductController` 的类文件。

```java
@RestController
@RequestMapping("/product")
public class ProductController {

    @PostMapping("/create")
    public Product createProduct(@RequestBody Product product) {
        return product;
    }
}
```

说明：

- `@RequestMapping("/product")` 设置主路由。
- `@PostMapping("/create")` 设置分路由。
- `@RequestBody` 表示从请求体读取 JSON 数据。

## 9. 创建 service 包

创建 `service` 文件夹，写接口文件，例如 `ProductService`。

```java
public interface ProductService {
    Product createProduct(Product product);
    void stockProduct(Long productId, Long quantity);
}
```

## 10. 创建 service/impl 实现类

在 `service` 包下创建 `impl` 文件夹，并创建实现类，例如 `ProductServiceImpl`。

```java
@Service
public class ProductServiceImpl implements ProductService {

    @Autowired
    private ProductRepository productRepository;

    @Override
    public Product createProduct(Product product) {
        Product savedProduct = productRepository.save(product);
        return savedProduct;
    }

    @Override
    public void stockProduct(Long productId, Long quantity) {
    }
}
```

## 11. 回到 Controller 调用 Service

```java
@RestController
@RequestMapping("/product")
public class ProductController {

    @Autowired
    private ProductService productService;

    @PostMapping("/create")
    public Product createProduct(@RequestBody Product product) {
        Product savedProduct = productService.createProduct(product);
        return savedProduct;
    }
}
```

注意：Controller 调用的是 `ProductService`，不是直接调用 `ProductRepository`。

## 12. 运行前检查

- 实体类是否添加 `@Getter` / `@Setter`。
- Repository 是否是接口。
- Service 接口和 impl 是否对应。
- Controller 是否注入 service。
- 数据库配置是否正确。
