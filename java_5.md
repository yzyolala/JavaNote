## Java 异常处理概览

### 1. Exception 是一个类
当程序有错误发生，JVM 会自动创建一个 exception 类。

### 2. 当 exception 发生时
程序会被中断。

### 3. 异常类中的方法
- `printStackTrace()` -> 提供异常名称、描述和堆栈跟踪。
- `toString()` -> 提供异常名称和描述。
- `getMessage()` -> 提供异常描述。

### 4. Runtime Stack Mechanism (运行时堆栈机制)
跟踪线程中的所有方法调用。

- 对于每个线程，JVM 创建一个运行时堆栈。
- 线程中执行的每个方法调用都存储在运行时堆栈中。
- 如果至少有一个方法异常终止，则程序终止也是异常终止。
- 所有方法执行完后，JVM 销毁运行时堆栈。

### 5. 继承体系
Object (所有 java 类的父类) -> Throwable 类：exception class & error class

| 异常类型  | 由程序编写  | 可恢复性    |
|-----------|------------|------------|
| Exception | 是         | 可恢复的    |
| Error     | 否         | 不可恢复的  |

- **Checked Exception** 和 **Unchecked Exception**
  - Checked Exception 指编译时就能被检测到的异常。
  - Unchecked Exception 指编译时无法被检测到的异常。

**各种异常**: 运行时异常、算术异常、空指针异常、下标越界异常、文件未找到异常。

> 注意：异常只会在运行时发生，无法在编译时发生。

```java
// Java Code Example
import java.io.*;

public class Example {
    // Checked Exception
    public static void readFromFile(String fileName) throws IOException {
        BufferedReader reader = new BufferedReader(new FileReader(fileName));
        String line = null;
        while ((line = reader.readLine()) != null) {
            System.out.println(line);
        }
        reader.close();
    }

    // Unchecked Exception
    public static int divide(int a, int b) {
        return a / b;
    }

    public static void main(String[] args) {
        // Checked Exception
        try {
            readFromFile("input.txt");
        } catch (IOException e) {
            System.err.println(e.getMessage());
        }

        // Unchecked Exception
        int result = divide(10, 0);
        System.out.println(result);
    }
}
```

### 6.错误(Error)：表示不可恢复的条件，如Java虚拟机(JVM)耗尽内存、内存泄漏、堆栈溢出错误、库不兼容、无限递归等。错误通常超出程序员的控制范围，我们不应该试图处理错误。

( Java virtual machine (JVM) running out of memory, memory leaks, stack overflow errors, library incompatibility, infinite recursion, etc.)

### 7.throws throw区别

throw关键字用于在代码中显式抛出异常，例如：

```java
public class Calculator {
    public static int divide(int dividend, int divisor) {
        if (divisor == 0) {
            throw new ArithmeticException("除数不能为零");
        }
        return dividend / divisor;
    }
}
```
在上面的例子中，如果divisor等于0，我们使用throw关键字抛出一个ArithmeticException异常，表示除数不能为零。

throws关键字用于在方法声明中指定可能抛出的异常类型，例如：
```java
public class FileUtil {
    public static String readLineFromFile(String filePath) throws IOException {
        BufferedReader reader = new BufferedReader(new FileReader(filePath));
        String line = reader.readLine();
        reader.close();
        return line;
    }
}
```
在上面的例子中，readLineFromFile方法声明中使用了throws关键字指定了可能抛出的IOException异常类型。

需要注意的是，无论是throw还是throws关键字，都不需要和try-catch块一起使用，但是它们经常与try-catch块搭配使用，以实现更完善的异常处理机制。
                                        
                                        
    
