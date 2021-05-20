# Path【路径】

静态类

> https://docs.microsoft.com/zh-cn/dotnet/api/system.io.path?redirectedfrom=MSDN&view=netframework-4.8

## 方法

- `GetFileName(str)` 返回指定路径字符串的文件名和扩展名。 也就是文件名
- `GetFileNameWithoutExtension(str)` 返回不具有**扩展名**的指定路径字符串的文件名
- `GetExtension(str)` 返回指定的路径字符串的扩展名 .
- `GetDirectoryName(str)` 返回指定路径字符串的目录信息
- `GetFullPath(str)` 返回指定路径字符串的绝对路径。
- `Combine(String, String)` 将两个字符串组合成一个路径。
- `GetPathRoot(str)` 获取指定路径的根目录信息
- `GetTempPath()`返回当前用户的临时文件夹的路径

## 使用

```c
Path.GetTempPath() //返回当前用户的临时文件夹的路径 
```

