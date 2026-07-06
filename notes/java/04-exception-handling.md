# Java 异常处理

## Exception 是什么

当程序发生错误时，JVM 会自动创建异常对象。异常发生时，程序正常执行流程会被中断。

常用方法：

| 方法 | 说明 |
| --- | --- |
| `printStackTrace()` | 输出异常名称、描述和堆栈跟踪 |
| `toString()` | 输出异常名称和描述 |
| `getMessage()` | 输出异常描述 |

## Runtime Stack Mechanism

运行时堆栈用于跟踪线程中的方法调用。

- 每个线程都有一个 JVM 创建的运行时堆栈。
- 每个方法调用都会被存入运行时堆栈。
- 如果至少一个方法异常终止，程序也会异常终止。
- 所有方法执行完后，JVM 销毁运行时堆栈。

## Throwable 继承体系

```text
Object
└── Throwable
    ├── Exception
    └── Error
```

| 类型 | 通常由程序处理 | 可恢复性 |
| --- | --- | --- |
| `Exception` | 是 | 可恢复 |
| `Error` | 否 | 通常不可恢复 |

常见异常：

- Runtime Exception
- Arithmetic Exception
- Null Pointer Exception
- Index Out Of Bounds Exception
- File Not Found Exception

注意：异常只会在运行时发生，不会在编译时真正“发生”。编译时只能检测某些异常是否需要处理。

## Checked Exception vs Unchecked Exception

| 类型 | 说明 | 是否需要声明/处理 |
| --- | --- | --- |
| Checked Exception | 编译时可检测，通常代表可预期情况 | 需要 `throws` 或 `try-catch` |
| Unchecked Exception | 编译时无法强制检测，通常由逻辑错误引起 | 不强制声明 |

```java
import java.io.*;

public class Example {
    public static void readFromFile(String fileName) throws IOException {
        BufferedReader reader = new BufferedReader(new FileReader(fileName));
        String line;
        while ((line = reader.readLine()) != null) {
            System.out.println(line);
        }
        reader.close();
    }

    public static int divide(int a, int b) {
        return a / b;
    }

    public static void main(String[] args) {
        try {
            readFromFile("input.txt");
        } catch (IOException e) {
            System.err.println(e.getMessage());
        }

        int result = divide(10, 0);
        System.out.println(result);
    }
}
```

## Error

`Error` 表示通常不可恢复的问题，例如：

- JVM 内存耗尽
- 内存泄漏
- Stack Overflow
- 库不兼容
- 无限递归

这类错误通常超出程序员可恢复处理范围，不应该像业务异常一样捕获处理。

## `throw` vs `throws`

### throw

`throw` 用于在代码中显式抛出异常。

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

### throws

`throws` 用于在方法声明中说明该方法可能抛出的异常类型。

```java
import java.io.*;

public class FileUtil {
    public static String readLineFromFile(String filePath) throws IOException {
        BufferedReader reader = new BufferedReader(new FileReader(filePath));
        String line = reader.readLine();
        reader.close();
        return line;
    }
}
```

`throw` 和 `throws` 不一定必须和 `try-catch` 同时出现，但经常搭配使用来构成完整的异常处理机制。
