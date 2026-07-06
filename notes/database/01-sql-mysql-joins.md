# SQL、MySQL 与 Join

## 启动 MySQL Server

在 terminal 中输入：

```bash
sudo /usr/local/mysql/support-files/mysql.server start
```

原笔记记录：

- `root` 密码：本机密码。
- local 数据库密码：`12345678`。

## SQL 语言分类

### DDL：Data Definition Language

DDL 用于定义和管理数据库对象结构，例如表、视图、索引、约束等。

常见命令：

- `CREATE TABLE`：创建新表。
- `ALTER TABLE`：修改表结构。
- `DROP TABLE`：删除表。
- `CREATE INDEX`：创建索引。

### DML：Data Manipulation Language

DML 用于操作表中的数据，保证数据一致性和完整性。

常见命令：

- `INSERT INTO`：插入新行。
- `UPDATE`：更新已有行。
- `DELETE FROM`：删除行。

### DQL：Data Query Language

DQL 用于查询和检索数据。

常见命令：

- `SELECT`：检索数据。
- `FROM`：指定查询表。
- `WHERE`：指定查询条件。
- `ORDER BY`：排序。
- `GROUP BY`：分组。

## Join 区别

示例表：

Customers 表：

| CustomerID | CustomerName |
| --- | --- |
| 1 | John |
| 2 | Emily |
| 3 | David |

Orders 表：

| OrderID | CustomerID |
| --- | --- |
| 101 | 1 |
| 102 | 2 |
| 103 | 2 |
| 104 | 4 |

### LEFT JOIN

左连接返回左表所有记录，以及右表中匹配的记录。如果右表没有匹配，结果中右表字段为 `NULL`。

```sql
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

结果：

| CustomerName | OrderID |
| --- | --- |
| John | 101 |
| Emily | 102 |
| Emily | 103 |
| David | NULL |

### RIGHT JOIN

右连接返回右表所有记录，以及左表中匹配的记录。如果左表没有匹配，结果中左表字段为 `NULL`。

```sql
SELECT Orders.OrderID, Customers.CustomerName
FROM Customers
RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

结果：

| OrderID | CustomerName |
| --- | --- |
| 101 | John |
| 102 | Emily |
| 103 | Emily |
| 104 | NULL |

### INNER JOIN

内连接只返回两个表中满足连接条件的记录。

### OUTER JOIN

外连接返回左表和右表中的所有记录，并在没有匹配时用 `NULL` 填充。外连接可分为左外连接和右外连接。
