# 启动mysql server

在terminal输入 sudo /usr/local/mysql/support-files/mysql.server start

**root密码**：本机密码

**local数据库密码**：12345678

# SQL语言可以分为以下三个主要部分：

**数据定义语言（DDL）**：
DDL用于定义和管理数据库对象的结构，例如表、视图、索引和约束等。DDL命令包括CREATE、ALTER和DROP等命令。通过DDL命令，可以创建新的数据库对象，修改现有对象的结构，或者删除不再需要的对象。

示例DDL命令：

CREATE TABLE：用于创建新表。
ALTER TABLE：用于修改现有表的结构。
DROP TABLE：用于删除表。
CREATE INDEX：用于创建索引。

**数据操作语言（DML）**：
DML用于对数据库中的数据执行操作，例如插入、更新和删除数据。DML命令可以更改表中的行数据，保证数据的一致性和完整性。

示例DML命令：

INSERT INTO：用于向表中插入新行。
UPDATE：用于更新表中的现有行。
DELETE FROM：用于删除表中的行。

**数据查询语言（DQL）**：
DQL用于查询和检索数据库中的数据。它允许用户根据特定的条件从表中提取数据，并支持各种查询操作，如排序、分组和聚合。

示例DQL命令：

SELECT：用于从表中检索数据。
FROM：指定要查询的表。
WHERE：用于指定查询条件。
ORDER BY：用于对结果进行排序。
GROUP BY：用于根据一列或多列对结果进行分组。
综上所述，DDL用于定义数据库对象的结构，DML用于操作数据，而DQL用于查询和检索数据。这些语言共同组成了SQL的核心功能，使得我们可以有效地管理和操作数据库。

# left join,right join,inner join,outer join的区别

**Left Join（左连接）**：
左连接返回左表中的所有记录，以及右表中与左表匹配的记录。如果右表中没有匹配的记录，则返回 NULL 值。左连接以左表为主导，将左表的所有记录与右表进行连接。
示例：
当我们有两个表 Customers（客户）和 Orders（订单）它们具有以下数据：

Customers 表
| CustomerID | CustomerName |
|------------|--------------|
| 1          | John         |
| 2          | Emily        |
| 3          | David        |

Orders 表
| OrderID | CustomerID |
|---------|------------|
| 101     | 1          |
| 102     | 2          |
| 103     | 2          |
| 104     | 4          |

使用左连接，我们可以获取所有客户以及他们的订单信息，即使他们没有订单。

查询语句：
```sql
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```
结果：
| CustomerName | OrderID |
|--------------|---------|
| John         | 101     |
| Emily        | 102     |
| Emily        | 103     |
| David        | NULL    |


**Right Join（右连接）**：
右连接与左连接类似，但是以右表为主导。右连接返回右表中的所有记录，以及左表中与右表匹配的记录。如果左表中没有匹配的记录，则返回 NULL 值。

当我们有两个表 Customers（客户）和 Orders（订单），它们具有以下数据：

Customers 表
| CustomerID | CustomerName |
|------------|--------------|
| 1          | John         |
| 2          | Emily        |
| 3          | David        |

Orders 表
| OrderID | CustomerID |
|---------|------------|
| 101     | 1          |
| 102     | 2          |
| 103     | 2          |
| 104     | 4          |

使用右连接，我们可以获取所有订单以及订单所属的客户信息，即使订单没有对应的客户。

查询语句：
```sql
SELECT Orders.OrderID, Customers.CustomerName
FROM Customers
RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

结果：

| OrderID | CustomerName |
|---------|--------------|
| 101     | John         |
| 102     | Emily        |
| 103     | Emily        |
| 104     | NULL         |


**Inner Join（内连接）**：
内连接只返回两个表中满足连接条件的记录。即只返回左表和右表中匹配的记录。

**Outer Join（外连接）**：
外连接返回左表和右表中的所有记录，并在没有匹配的记录时使用 NULL 值填充。外连接分为左外连接和右外连接两种情况。

