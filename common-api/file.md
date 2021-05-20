### File【文件】

静态类

> https://docs.microsoft.com/zh-cn/dotnet/api/system.io.file?redirectedfrom=MSDN&view=netframework-4.8

## 方法

- `Create(path,filename)` 在指定路径中创建或覆盖文件。

- `Delete(path)` 删除指定的文件。

- `Copy(String, String)` 将现有文件复制到新文件。 不允许覆盖同名的文件。

- `Copy(String, String, Boolean)` 将现有文件复制到新文件。 允许覆盖同名的文件。

- `Exists(path)` 确定指定的文件是否存在

- `Move(path,newPaht)` 将指定文件移到新位置，新路径中必须包含原文件名。

  ```csharp
  File.Move(@"C:\Users\zyrbx\Desktop\火绒安全.png", @"C:\Users\zyrbx\Desktop\Test\火绒安全.png");
  ```

- ReadAllBytes(Paht) 打开一个文件，将文件的内容读入一个字节数组，然后关闭该文件。 返回值字节数组

  ```csharp
  byte[] file = File.ReadAllBytes(@"C:\Users\zyrbx\Desktop\a.txt");
              string str = Encoding.UTF8.GetString(file);//编码
              Console.WriteLine(str);
  ```

- `WriteAllBytes(path,byte[])` 创建一个新文件，在其中写入指定的字节数组，然后关闭该文件。 如果目标文件已存在，则覆盖该文件。

  ```csharp
  File.WriteAllBytes(@"C:\Users\zyrbx\Desktop\b.txt", Encoding.UTF8.GetBytes("我w爱发明"));
  ```

- `WriteAllLines(path,String[])` **创建**一个新文件，在其中写入指定的字符串数组，然后关闭该文件。

- `WriteAllText(path, String)` 创建一个新文件，在其中写入指定的字符串，然后关闭文件。 如果目标文件已存在，则覆盖该文件。

- `WriteAllText(path, String, Encoding)` 创建一个新文件，在其中写入指定的字符串，然后关闭文件。 如果目标文件已存在，则覆盖该文件。

- `AppendAllText(path, String)` 打开一个文件，向其中追加指定的字符串，然后关闭该文件。 如果文件不存在，此方法创建一个文件，将指定的字符串写入文件，然后关闭该文件。

- `AppendAllText(path, String, Encoding)` 将指定的字符串追加到文件中，如果文件还不存在则创建该文件。

- `ReadAllLines(String)` 打开一个文本文件，读取文件的所有行，然后关闭该文件。返回字符串数组

- `ReadAllLines(String, Encoding)` 打开一个文件，使用指定的编码读取文件的所有行，然后关闭该文件。 返回字符串数组

- `ReadAllText(String)` 打开一个文本文件，读取文件的所有行，然后关闭该文件。 返回值字符串

- `ReadAllText(String, Encoding)` 打开一个文件，使用指定的编码读取文件的所有行，然后关闭该文件。 返回值字符串。