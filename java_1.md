### Java 开发基础

- JDK=JRE（JVM + libraries
） + Javac（编译器：将Java源代码编译成JVM执行的字节码文件） + 开发工具

|       属性       |              JDK               |                   JRE                  |         JVM         |
|-----------------|-------------------------------|---------------------------------------|--------------------|
| **基本定义**    | 软件开发工具包                 | 允许 Java 程序运行的软件包             | 执行字节码文件     |
| **组成部分**    | JRE + javac + development tools| JVM + libraries                        | N/A                |
| **功能**        | 开发、调试等                    | 运行 Java 程序、包含类库和其他支持文件 | 执行字节码          |
| **附加工具**    | 包含 javac                      | 不包含 javac                           | 不包含软件开发工具  |
| **安装程序**    | 附带安装程序                    | 只包含执行源代码的环境                 | 包含在 JDK 和 JRE 中|


### 编程基础

- **Identifiers**: Any name(class name, method name, variables etc.) in a java program
- **1 byte = 8 bits**

### 数据类型

- **原始数据类型**（8种）：
    - byte,short,int,long,float,double,char,boolean

- **按照占用内存空间大小排序**：
    - double(8 bytes)=long(8 bytes)>float(4 bytes)>int(4 bytes)>short(2 bytes)=char(2 bytes)>byte(1 byte)>boolean(usually occupy 1 byte)
- **强制类型转换也按照这个顺序**

### 类型转换

- **小->大**: 自动转换
- **大->小**: 强制转换

### 常用数据类型

- **小数一般用double，整数一般用int**
