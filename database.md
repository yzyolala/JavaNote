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
