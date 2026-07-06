# Maven 与 JPA

## Group ID 和 Artifact ID

Maven 中的 `groupId` 和 `artifactId` 用于唯一标识项目。

### Group ID

`groupId` 表示项目所属组织或团队的唯一标识，通常使用反向域名格式。

示例：

```text
com.example
```

### Artifact ID

`artifactId` 表示项目本身的唯一标识，通常是项目名称或缩写。

总结：

- `groupId` 指组织或团队。
- `artifactId` 指项目本身。
- 二者共同构成 Maven 项目的唯一标识。

## 创建 Maven 项目

创建 Maven 项目时可选择：`quick start`。

## Maven 生命周期

| 命令 | 说明 |
| --- | --- |
| `compile` | 编译所有源代码文件，生成 `.class` 文件 |
| `package` | 构建应用程序并创建可部署的 jar 文件 |
| `install` | 构建并将 jar 安装到本地仓库 |
| `clean` | 删除已生成的 jar 文件和 `target` 文件夹 |

## JPA

JPA = Java Persistence API。

JPA 是管理对象和数据库关系映射的规范，提供了一套标准接口和方法来实现数据持久化操作。

通过 JPA，开发人员可以使用面向对象方式操作数据库，不需要直接编写原始 SQL 查询。它在应用和数据库之间提供抽象层，让开发者更专注业务逻辑。

支持 JPA 的常见产品包括：

- Hibernate
- EclipseLink
- TopLink
- Spring Data JPA
