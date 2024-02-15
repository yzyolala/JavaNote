## Java 开发基础

### 1. 工具和环境

- **javac**: 就是compiler
- **JDK**: 等于 JRE + javac + development tools
- **JRE**: 等于 JVM + libraries（JRE 不包含 javac）

### 2. 工具和环境的定义

- **JDK**: 是一个软件开发工具包
- **JRE**: 是一个软件包，允许 Java 程序运行
- **JVM**: 是一个用于执行字节码文件

### 3. 工具的功能

- **JDK**: 包含用于开发、调试等的工具
- **JRE**: 包含类库和其他支持文件
- **JVM**: 中不包含软件开发工具

### 4. 安装和运行环境

- **JDK**: 附带安装程序
- **JRE**: 只包含执行源代码的环境
- **JVM**: 包含在软件 JDK 和 JRE 中

- ## Java 组件对比

|       属性       |              JDK               |                   JRE                  |         JVM         |
|-----------------|-------------------------------|---------------------------------------|--------------------|
| **基本定义**    | 软件开发工具包                 | 允许 Java 程序运行的软件包             | 执行字节码文件     |
| **组成部分**    | JRE + javac + development tools| JVM + libraries                        | N/A                |
| **功能**        | 开发、调试等                    | 运行 Java 程序、包含类库和其他支持文件 | 执行字节码          |
| **附加工具**    | 包含 javac                      | 不包含 javac                           | 不包含软件开发工具  |
| **安装程序**    | 附带安装程序                    | 只包含执行源代码的环境                 | 包含在 JDK 和 JRE 中|



### 5. 编程基础

- **Identifiers**: Any name(class name, method name, variables etc.) in a java program
- **1 byte = 8 bits**

### 6. 数据类型

- **原始数据类型**：（8种）：
    - byte,short,int,long,float,double,char,boolean

### 7. 数据类型和内存

- **按照占用内存空间大小排序**：
    - double(8 bytes)=long(8 bytes)>float(4 bytes)>int(4 bytes)>short(2 bytes)=char(2 bytes)>byte(1 byte)>boolean(usually occupy 1 byte)
- **强制类型转换也按照这个顺序**

### 8. 类型转换

- **小->大**: 自动转换
- **大->小**: 强制转换

### 9. 常用数据类型

- **小数一般用double，整数一般用int**
