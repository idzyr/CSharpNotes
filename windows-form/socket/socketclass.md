# Socket类

提供socket对象。

> https://docs.microsoft.com/zh-cn/dotnet/api/system.net.sockets.socket?redirectedfrom=MSDN&view=netframework-4.8

## 构造方法

- `Socket(AddressFamily, SocketType, ProtocolType)`使用指定的地址族、套接字类型和协议初始化 Socket 类的新实例。

  - 参数

    - AddressFamily 指定 Socket 用来解析地址的寻址方案。例如，InterNetwork 指示当 Socket 使用一个 IP 版本 4 地址连接。 

    - SocketType 定义要打开的 **Socket** 的类型 SocketType是一个枚举类型，常用SocketType.Stream流类型打开socket。

    - ProtocolType 是一个枚举类型告诉Windows Sockets API 所请求的协议是TCP/UDP。

## 属性

- `RemoteEndPoint` 获取远程终结点。客户端的IP和端口号。

## 方法

- `Accept()` 为新建连接创建**新的 Socket对象**。
- `Bind()` 使 Socket 与一个本地终结点【一个IPEndPoint类实例对象包含IP和端口 】相关联。
- `Listen(int)` 将 Socket 置于侦听状态。并设置监听队列，队列表示同一时间点最多客户端连接数。
- `Close()` 关闭 Socket 连接并释放所有关联的资源。
- `Receive()` 接收客户端发送的数据，【通讯socket调用此方法】
- `Connect(IP)` 建立与远程主机的连接。
- `Send(Byte[])` 将数据发送到连接的 Socket 【发送数据到客户端/服务端】