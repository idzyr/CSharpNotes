# IPEndPoint类

将网络端点表示为 IP 地址和端口号。IP地址和端口号对象。

> https://docs.microsoft.com/zh-cn/dotnet/api/system.net.ipendpoint?redirectedfrom=MSDN&view=netframework-4.8

## 构造方法

- `IPEndPoint(IPAddress, Int32)` 用指定的地址和端口号初始化 IPEndPoint 类的新实例。
  - 参数
    1. IPAddress 一个IP地址对象。使用PAddress 类构造的实例对象。
    2. Int32 端口号 1 ~ 65535之间 最好从1024以上开始。

