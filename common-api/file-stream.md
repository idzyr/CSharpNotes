# FileStream【文件字节缓冲流】

## 构造方法

- `FileStream(Path, FileMode.OpenOrCreate, FileAccess.Read)`
  - 参数
    1. Paht 操作文件路径
    2. FileMode 以什么方式打开该文件（OpenOrCreate 没有文件就创建一个后打开不无异常）
    3. FileAccess 对文件中的数据进行什么操作（Read 读取文件）

## 方法

- `Read(Byte[],int,int)` 从流中读取字节块并将该数据写入给定缓冲区中。

  - 参数

    1. (Byte[] 字节缓冲区数组。用来存放读取的数据。
    2. int 从字节缓冲数组中的那个索引出开始存放数据。
    3. int 读入缓冲区中的总字节数。

  - 返回值

    int 读入缓冲区中的总字节数(也就是每次读取的有效字节数)。 如果当前的字节数没有所请求那么多，则总字节数可能小于所请求的字节数；如果已到达流的末尾，**则为零**。

- `Close()` 关闭流

- `Dispose()` 释放由 Stream 占用的所有资源

- `Write(Byte[],int,int)`使用从缓冲区读取的数据,写入到指定的文件中。

  - 注意要使用此方法构造方法中的FileAccess 要选择Write
  - 参数
    1. (Byte[] 字节缓冲数组，存放要写入文件的数据，字节数组。
    2. int 从字节缓冲数组中的那个索引出开始读取数据
    3. int 写入缓冲区中的总字节数。

## using

在using当中，会自动的帮助我们释放流所占用的资源。

**格式**

```c
using(//创建FileStream对象)
{
    //对文件的操作代码

}
```

## 使用

- 写入

  ```c
  //使用FileStream来写入数据
  using (FileStream fsWrite = new FileStream(@"C:\Users\zyrbx\Desktop\new.txt", FileMode.OpenOrCreate, FileAccess.Write))
  {
      string str = "看我游牧又把你覆盖掉";
      byte[] buffer = Encoding.UTF8.GetBytes(str);//字符串转字节数组
      fsWrite.Write(buffer, 0, buffer.Length);
  }
  ```

- 文件复制

  ```c
          #region 文件复方法
          /// <summary>
          /// 文件复制
          /// </summary>
          /// <param name="source">原文件路径</param>
          /// <param name="target">目标路径</param>
          /// <returns>复制完成返回true</returns>
          public static bool CopyFiles(string source,string target)
          {           //创建文件输入流
              using (FileStream fsRead = new FileStream(source,FileMode.OpenOrCreate,FileAccess.Read) )
              {   //创建文件输出流
                  using (FileStream fsWrite = new FileStream(target,FileMode.OpenOrCreate,FileAccess.Write))
                  {   //字节缓冲数组。用来存放读取到的字节。
                      byte[] buffStream = new byte[1024 * 1024 * 5];
  
                      while (true)
                      {       //读取文件，存入到字节数组中。
                              //byteLenght 存放读取的有效字节数。
                          int byteLenght = fsRead.Read(buffStream, 0, buffStream.Length);
                          //读取到文件到达流的末尾，跳出循环。
                          if (byteLenght == 0)
                          {
                              break;
                          }
                          //开始写入文件
                          fsWrite.Write(buffStream,0,byteLenght);
                      }
                  }//写入using
              }//读取using
              return true;
          }//方法结束
  
          #endregion
  ```

