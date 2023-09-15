## Java 编程基础

### 1. 对象和类

- **对象**: Objects are instances of class - it is the actual one that holds the memory.
  - **注释**: 创建的对象储存在内存中

### 2. 源文件结构 (Source File Structure)

- **.java文件** 包含以下几部分：
  - **Package statement**: at most 1
  - **import**: Any number of imports
  - **class/interface/enum**

### 3. 类的组成

- **Class**: variables + methods

### 4. 方法语法 (Method Syntax)

```java
AccessModifier returnType methodName(dataType variable, …..){ 
  // code return something; 
}
```

### 5. 导入 (Import)

- **显式导入**: `import java.util.Scanner;`
- **隐式导入**: `import java.util.*;`

### 6. 类的数量和规则

- Java程序可以有任意数量的类
  - 但最多只能有一个类是 `public` 的
  - 程序的名称应该是公共类的名称
  - 对于每个Java类，都会生成一个 `.class` 文件。因此可以单独运行每个类

