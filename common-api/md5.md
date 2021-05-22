# MD5

MD5是用来加密字符内容，通过用做对密码的加密。

是一个抽象类。

## 方法

- `Create()` 创建 MD5 哈希算法的默认实现的实例。

## 使用

```c
//对应     202cb962ac59075b964b07152d234b70
            //自己加密  202cb962ac59075b964b07152d234b70
            string str = "123";

            //返回md5抽象类的实例类对象。
            MD5 md5 = MD5.Create();

            //把字符串转为byte数组
            byte[] bstr = Encoding.UTF8.GetBytes(str);

            //接收加密后的字节数组。
            byte[] md5Byte = md5.ComputeHash(bstr);
            /*参数
             *  - 需要一个byte数组。
             *返回
             *  - 返回一个加密后的byte[]
             */

            string newStr = null;
            /* 对每一个加密后的字节数组中的元素执行ToString()；方法，
             * 如果对整个数组执行此方法会把整体进行解析得不到我们需要的*/

            foreach (byte item in md5Byte)
            {
                //这样操作放回的是10进制的字符串不是我们需要的16进制
                //newStr += item.ToString();//返回结果3244185981728979115075721453575112
                newStr += item.ToString("x2");//转换为小写16进制保留两位

            }
```

