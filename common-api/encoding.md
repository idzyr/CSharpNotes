### Encoding【字符编码】

字符编码

> https://docs.microsoft.com/zh-cn/dotnet/api/system.text.encoding?redirectedfrom=MSDN&view=netframework-4.8

## 属性

- `Default` 获取操作系统的当前 ANSI 代码页的编码
- `UTF-8` 获取 UTF-8 格式的编码。

## 方法

- `GetString(Byte[])` 在派生类中重写时，将指定字节数组中的所有字节解码为一个字符串
- `GetString(Byte[],int index,int count)` 在派生类中重写时，将指定字节数组中的所有字节解码为一个字符串
  - 参数
    1. Byte[] 要解码的字符数组
    2. int index 解码的起始索引
    3. int count 解码的结束索引。
- `GetBytes(String)` 在派生类中重写时，将指定字符串中的所有字符编码为一个字节序列
- `GetEncoding(String)` 返回与指定代码页名称关联的编码。
  - 参数
    1. String 一种编码UTF-8 等。

## 使用

```c
//        编码表    字节数组
Encoding.UTF8.GetString(byte[])//按指定编码把字节数组转字符串。

   //通过命名空间使用Encoding类型。把字符串转为字节数组
                byte[] buffer = System.Text.Encoding.Default.GetBytes(str);
```

