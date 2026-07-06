# JPA 注解、关系映射与 Spring Boot 分层

## Cascade

### `@OneToOne(cascade = CascadeType.ALL)`

当对 `User` 对象执行持久化操作时，关联的 `Profile` 对象也会被同时保存。类似地，对 `User` 执行更新、删除等操作时，关联对象也会受到相同操作影响。

### `CascadeType.PERSIST` vs `CascadeType.ALL`

| 类型 | 说明 |
| --- | --- |
| `CascadeType.PERSIST` | 只在持久化时自动保存关联实体 |
| `CascadeType.ALL` | 保存、更新、删除等所有操作都级联处理关联实体 |

## `@JoinTable`

```java
@JoinTable(
    name = "student_course",
    joinColumns = @JoinColumn(name = "student_id", referencedColumnName = "id"),
    inverseJoinColumns = @JoinColumn(name = "course_id", referencedColumnName = "id")
)
```

说明：

- `name = "student_course"`：指定关联表名称。
- `joinColumns`：定义当前实体在关联表中的外键列。
- `name = "student_id"`：关联表中表示学生 ID 的列名。
- `referencedColumnName = "id"`：学生实体表中的主键列名。
- `inverseJoinColumns`：定义另一方实体在关联表中的外键列。
- `name = "course_id"`：关联表中表示课程 ID 的列名。
- `referencedColumnName = "id"`：课程实体表中的主键列名。

## `@ManyToMany(mappedBy = "courses")`

`mappedBy = "courses"` 指定多对多关系由另一个实体类中的 `courses` 属性维护。

作用：告诉 JPA 当前实体不是关系拥有方，不需要在当前实体中再创建额外的关联表或关联列。

`@JoinTable` 和 `mappedBy` 常一起用于双向多对多关系：

- 一方用 `@JoinTable` 定义关联表和关联列。
- 另一方用 `mappedBy` 指向关系拥有方的属性。

## `@GeneratedValue` 策略

### `GenerationType.AUTO`

把主键生成策略交给持久化引擎。JPA 默认策略通常就是 `AUTO`，可以显式写：

```java
@GeneratedValue(strategy = GenerationType.AUTO)
```

也可以简写：

```java
@GeneratedValue
```

### `GenerationType.IDENTITY`

通常用于支持自增列的数据库，例如 MySQL 的 `AUTO_INCREMENT`。

```java
@GeneratedValue(strategy = GenerationType.IDENTITY)
```

重点：选择自增长策略后，创建 setter 方法或 constructor 时不要涵盖该主键参数。

## `@OneToMany` 使用套路

主表属性通常使用 `@OneToMany`，并搭配另一个表属性的 `Set` 集合。

```java
@OneToMany(mappedBy = "student")
Set<Vehicle> vehicles = new HashSet<>();
```

副表属性通常使用 `@ManyToOne`，并搭配 `@JoinColumn` 规定外键列。

```java
@ManyToOne
@JoinColumn(name = "s_id", referencedColumnName = "id")
Student student;
```

总结：`@OneToMany` 一般搭配 `mappedBy` 设置主导方，不搭配 `@JoinColumn`。

## `@OneToOne` 使用套路

通常不需要使用 `mappedBy`。在 `@OneToOne` 关系中，有主导方和从属方：

- 主导方负责维护关联关系。
- `@JoinColumn` 通常与 `@OneToOne` 一起使用，用于指定关系拥有方实体中的外键列。

总结：`@OneToOne` 一般搭配 `@JoinColumn`，不搭配 `mappedBy`。

## `@ManyToOne` 使用套路

`@ManyToOne` 一般可选搭配 `@JoinColumn`，不搭配 `mappedBy`。

## 关系注解总结

| 注解 | 搭配 `mappedBy` | 搭配 `@JoinColumn` |
| --- | --- | --- |
| `@OneToMany` | 是 | 否 |
| `@OneToOne` | 否 | 是 |
| `@ManyToOne` | 否 | 可选 |

## Repository 的作用

Repository 文件用于定义数据访问接口和方法。通过这些方法可以进行常见 CRUD 操作。

它隐藏底层数据库细节，并提供面向对象的方式操作数据。

```java
@Repository
public interface ProductRepository extends CrudRepository<Product, Long> {
}
```

说明：

- `extends CrudRepository<Product, Long>` 表示继承 CRUD 功能接口。
- 第一个泛型是实体类。
- 第二个泛型是实体类主键类型。

## Spring Boot 项目结构

### repository

放 repository 接口文件。

### service

包含：

1. `xxxService` 接口文件，用于定义方法。
2. `impl` 文件夹，放实现类。
3. impl 类实现 service 接口，并通过 repository 完成具体逻辑。

### model

放实体类。常见注解：

- `@Entity`
- `@Getter`
- `@Setter`
- `@Id`
- `@GeneratedValue(strategy = GenerationType.IDENTITY)`
- `@OneToMany`

### controller

负责定义路由并调用 service。

常见注解：

- `@RestController`
- `@RequestMapping`
- `@PostMapping`

```java
@RestController
@RequestMapping("/customer")
public class CustomerController {

    @Autowired
    private CustomerService customerService;

    @PostMapping("/register")
    public Customer registerCustomer(@RequestBody Customer customer) {
        Customer saved = customerService.registerCustomer(customer);
        return saved;
    }
}
```

## `@PathVariable` 和 `@RequestBody`

### `@PathVariable`

从路径中获取变量。

```java
@DeleteMapping("/cancel/{id}")
public String cancelOrder(@PathVariable Long id) throws OrderNotFoundException {
    return orderService.cancelOrder(id);
}
```

这里从 `/cancel/{id}` 中获取变量 `id`。

### `@RequestBody`

从请求体中获取 JSON 数据。

```java
@PostMapping("/updateaddress/{id}")
public Order updateAddress(@PathVariable Long id, @RequestBody Address address)
        throws OrderNotFoundException {
    Order updateOrder = orderService.updateAddress(id, address);
    return updateOrder;
}
```

表示从路径拿 `id`，同时从请求体传入 JSON 格式的新内容。
