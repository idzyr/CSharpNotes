# String【字符串】

## 属性

- `Length` //获得字符串的长度或字符个数。

## 方法

- `ToUpper():`将字符转换成大写形式

- Equals(要比较的字符串,StringComparison.OrdinalIgnoreCase):比较两个字符串，可以忽略大小写。

  StringComparison 枚举类型，指定将如何去比较这个字符串。

- Split(char[]数组以那些字符做分割,返回值是否包含空字符串),：分割字符串，返回字符串类型的数组

  ```csharp
   string s = "a b   dfd _   +    =  ,,, fdf ";
              //分割字符串Split
    char[] chs = { ' ', '_', '+', '=', ',' };//定义使用原字符串中的那些字符串来分割字符
    string[] str = s.Split(chs,StringSplitOptions.RemoveEmptyEntries);
  StringSplitOptions.RemoveEmptyEntries//返回值不包括空字符串。
  ```

- Replace(“要替换的字符串”,“新字符串”):将字符串中某个字符串替换成一个新的字符串

- Substring(开始索引,截取字符个数)：截取字符串。

- `EndsWith(“string”):`判断以字符结束

- `StartsWith(“stirng”):`判断以字符开始

- IndexOf(str,搜索起始索引):判断某个字符串在字符串中第一次出现的位置，如果没有返回-1、值类型和引用类型在内存上存储的地方不一样。

- `LastIndexOf(str)：`判断某个字符串在字符串中最后一次出现的位置，如果没有同样返回-1

- `Trim():`去掉字符串中前后的空格

- `TrimEnd()`：去掉字符串中结尾的空格

- `TrimStart()`：去掉字符串中前面的空格

- `string.IsNullOrEmpty():`判断一个字符串是否为空或者为null

- string.Join(以什么字符连接,string[])：将数组按照指定的字符串连接，返回一个字符串。

