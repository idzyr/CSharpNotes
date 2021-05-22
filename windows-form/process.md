# 进程

> https://docs.microsoft.com/zh-cn/dotnet/api/system.diagnostics.process?redirectedfrom=MSDN&view=netframework-4.8

Process管理进程的类。

## 方法

### 静态

- `GetProcesses()`获取计算机上运行的所有进程。**静态方法**
- `Kill()` 立即停止关联的进程杀死进程。
- `Start(“”)`打开一个进程，可以打开程序，**文件目录，网页等**
- `Start(String)` 通过指定文档或应用程序文件的名称来启动进程资源，并将资源与新的 Process 组件关联。