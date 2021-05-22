# StreamReader【字符缓冲输入流】

> https://docs.microsoft.com/zh-cn/dotnet/api/system.io.streamreader?redirectedfrom=MSDN&view=netframework-4.8

读取字符串

## 构造方法

- `StreamReader(Path,Encoding)`

## 属性

- `CurrentEncoding` 获取当前 StreamReader 对象正在使用的当前字符编码。
- `EndOfStream` 获取一个值，该值表示当前的流位置是否在流的末尾。

## 方法

- `ReadLine()` 从当前流中读取一行字符并将数据作为字符串返回。

