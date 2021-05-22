### Directory【目录/文件夹】

操作目录的类,**静态类**

> https://docs.microsoft.com/zh-cn/dotnet/api/system.io.directory?redirectedfrom=MSDN&view=netframework-4.8

## 方法

- `Delete(path)` 从指定路径删除空目录
- `Delete(path, Boolean)` 删除指定的目录并（如果指示）删除该目录中的所有子目录和文件
- `Move()` 将文件或目录及其内容移到新位置。
- `GetFiles(path)` 返回指定目录中文件的名称（包括其路径）。
- `GetFiles(path, String)` 返回指定目录中与指定的搜索模式【通配符】匹配的文件的名称（包含其路径）
- `GetDirectories(path)` 返回指定目录中的子目录的名称（包括其路径）。
- `GetDirectories(path, String)` 返回指定目录中与指定的搜索模式匹配的子目录的名称（包括其路径）。
- `CreateDirectory(path)` 在指定路径中创建所有目录和子目录，除非它们已经存在。
- `Exists()` 确定给定路径是否引用磁盘上的现有目录。

