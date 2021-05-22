# 线程

每个进程是有多个线程组成的。

Thread 线程类，是一个密封类，不可以被其它继承。

> https://docs.microsoft.com/zh-cn/dotnet/api/system.threading.thread?redirectedfrom=MSDN&view=netframework-4.8

## 构造函数

- Thread(要执行的方法【不用带括号】) 初始化线程类并传递一个要执行的任务，

  - 执行的方法带参数

    要执行的方法有参数那么参数**必须是object类型。**参数传递从start()方法传递。

    ```csharp
    Thread thread = new Thread(Test);//创建新线程执行Test方法。
    thread.Start(1);//标记当前线程可以被执行了，并给传递Test方法传递参数
    
    public void Test (object n){
        ....
    }
    ```

## 属性

- `IsBackground` 获取或设置一个值，该值指示**某个线程是否为后台线程**
- `Name` 获取或设置线程的名称。
- `CurrentThread` 获取当前正在运行的线程。

## 方法

- `Start()` **标记**这个线程准备就绪了，可以随时被执行
- `Abort()` 终止线程。 终止完成后不能再Start();

### 静态

- `Sleep(Int32)` 将当前线程挂起指定的毫秒数。 让当前线程停止一段时间运行。

## 线程的分类

### 前台线程

只有所有的前台线程**都关闭**程序才会关闭。**默认创建的线程都是前台线程。**

### 后台线程

只要前台线程结束了，后台线程**自动**结束。

## 注意

在.Net下，是不允许跨线程的访问。不过可以使用 `Control.CheckForIllegalCrossThreadCalls`欺骗一下，达到跨线程访问。

```csharp
//取消检查跨线程的访问
            Control.CheckForIllegalCrossThreadCalls = false;
```

