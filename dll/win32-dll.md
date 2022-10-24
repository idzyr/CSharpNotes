# 调用Win32DLL

> win32API参考
>
> https://docs.microsoft.com/zh-cn/windows/win32/api/_winmsg/

win32有两种编码的api分别是**ANSI**和**Unicode**默认调用是**ANSI**

1. 添加命名空间

```csharp
//使用平台调用技术进行互操作性之前，首先需要添加这个命名空间
using System.Runtime.InteropServices;
```

2. 在类中导入方法所在DLL

- 常见DLL
  - User32.dll
  - kernel32.dll

```csharp
[DllImport("kernel32.dll")]
```

3. 声明方法 **必须添加的修饰符**`static `和 `extern `**方法名和win32API中定义的一致。参数个数和类型也要一致。**

```c
public static extern bool Beep(int frequency, int duration);
```



## 不同编码API声明方式；

- 第一种指定方式，通过**CharSet字段指定**

  ```csharp
  [DllImport("user32.dll", CharSet = CharSet.Unicode)] //调用Unicode版本
          public static extern int MessageBox(IntPtr hWnd, String text, String caption, uint type);
  ```

- 第二种通过，**EntryPoint字段指定**

  - 方法后面带A表示**ANSI**版本

    ```csharp
     [DllImport("user32.dll", EntryPoint="MessageBoxA")] //ANSI版
                   public static extern int MessageBox3(IntPtr hWnd, String text, String caption, uint type);
    ```

  - 方法后面带W表示**Unicode**版本

    ```csharp
     [DllImport("user32.dll", EntryPoint = "MessageBoxW")]//Unicode版
                   public static extern int MessageBox4(IntPtr hWnd, String text, String caption, uint type);
    ```

    



## C++转C#参数类型对照

| C++                           | C#       | 备注                                           |
| ----------------------------- | -------- | ---------------------------------------------- |
| HWND，LRESULT，WPARAM，LPARAM | `IntPtr` | IntPtr：用于表示**指针或句柄**的平台特定类型。 |
| LPCTSTR，LPCSTR               | `String` |                                                |
| UINT                          | `uint`   | uint：无符号 32 位整数范围0 到 4,294,967,295   |
| DWORD                         | `int`    |                                                |

更多类型详解[C#与C++之间类型对照](../appendix/type-correspondence.md)

## 调用示例

```csharp
using System.Runtime.InteropServices; //使用平台调用技术进行互操作性之前，首先需要添加这个命名空间
namespace Windows32APITest
{    
public partial class Form1 : Form
    {
     //加载dll声明方法
        [DllImport("user32.dll")] //默认使用的是ANSI所以可以不指定
        public static extern int MessageBox(IntPtr hWnd, String text, String caption, uint type);

        public Form1()
        {
            InitializeComponent();
             MessageBoxA(new IntPtr(0),"内容","Win32",0); //调用方法。
        }

    }
}
```

