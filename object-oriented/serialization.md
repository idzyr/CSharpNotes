# 序列化和反序列化

注要用于传输数据。

## 序列化

就是将对象转换为二进制

- 将类标记为可以被序列化的[Serializable]

  ```c
  [Serializable] //标记后证明这个类可以被序列化
  public class Test {
  
  }
  ```

- 使用BinaryFormatter类对象把object写入到指定路径下。

  ```c
  //创建一个文件输出流。
  using (FileStream fsWrite = new FileStream(path", FileMode.OpenOrCreate, FileAccess.Write))
  { 
          //开始序列化对象
        BinaryFormatter bf = new BinaryFormatter();//创建BinaryFormatter对象
        bf.Serialize(fsWrite, Test);//开始序列化对象。
      //Serialize()方法参数。
      //  一个输出流(二进制流这里直接使用using中创建的输出流即可)；
      //要序列化的对象。
  }
  ```

## 反序列化

就是将二进制转换为对象

```c
Test t; //存放反序列化得到的对象。
//创建文件输入流对象。
using (FileStream fsRead = new FileStream(path, FileMode.OpenOrCreate, FileAccess.Read))
{
    //创建反序列化对象。
    BinaryFormatter bf = new BinaryFormatter();
    t = (Test)bf.Deserialize(fsRead);
    //使用Deserialize();方法开始反序列化
    //参数，输入流（要读取对象的流，这里直接写using中创建的输入流）
    //返回值是object类型，我们要转换为，原序列化对象类型。使用强转。
}
```

