# GroupID和ArtifactID

Maven Group ID (GroupID) 和 Artifact ID (ArtifactID) 是 Maven 项目中两个不同的标识符，用于唯一标识一个特定的项目。

Group ID 是指项目所属的组织或者团队的唯一标识符。它通常以反向域名的形式表示，用于区分不同组织或者团队的项目。例如，如果你的组织域名是example.com，那么你的 Group ID 可以是 com.example。

Artifact ID 是指项目本身的唯一标识符。它用于区分同一个组织或者团队下不同项目的不同版本。Artifact ID 可以是任意的字符串，通常是项目的名称或者缩写。

总结起来，Group ID 是指代组织或者团队，Artifact ID 是指代项目本身。它们共同构成了 Maven 项目的唯一标识符。

# 创建maven项目

选择：quick start

# maven生命周期

compile: 编译所有源代码文件生成类文件
package: 构建应用程序并创建一个可部署的jar文件
install: 构建并将jar文件安装到本地仓库
clean: 删除已生成的jar文件（删除target文件夹）

# JPA

在Java中，JPA代表Java持久化API（Java Persistence API）。JPA是一种用于管理对象和数据库之间关系映射的规范，它提供了一套标准的接口和方法来实现数据持久化操作。

通过JPA，开发人员可以使用面向对象的方式来操作数据库，而不需要编写原始的SQL查询语句。它简化了与数据库的交互，提供了一种抽象层，使开发人员能够更专注于业务逻辑而不必过多关注底层的数据库操作细节。

各种企业供应商（如Oracle、Redhat、Eclipse等）通过在其中添加JPA持久化功能来提供新产品。其中一些产品包括：Hibernate、Eclipselink、Toplink、Spring Data JPA等。


