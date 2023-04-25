1.  javac就是complier

2.  JDK=JRE+javac and development tools

    JRE=JVM+libraries
  
    JRE不包含javac
  
  
3.  JDK 是一个软件开发工具包

    JRE 是一个软件包，允许 Java 程序运行
  
    JVM 是一个用于执行字节码文件
  
  
4.  JDK 包含用于开发、调试等的工具
  
    JRE 包含类库和其他支持文件
    
    JVM 中不包含软件开发工具

5.  JDK 附带安装程序
  
    JRE 只包含执行源代码的环境
  
    JVM 包含在软件 JDK 和 JRE 中
    
6.  Identifiers:Any name(class name, method name, variables etc.) in a java program 

7.  1 byte = 8 bits

8.  原始数据类型：（8种）：

    byte,short,int,long,float,double,char,boolean

9.  按照占用内存空间大小排序：
    
    double(8 bytes)>float(4 bytes)>long(8 bytes)>int(4 bytes)>short(2 bytes)=char(2 bytes)>byte(1 byte)>boolean(usually occupy 1 byte)
    
    强制类型转换也按照这个顺序
    
10.  小->大：自动转换

     大->小：强制转换
     
11.  小数一般用double，整数一般用int

