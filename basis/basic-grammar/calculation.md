# 运算符

和其它语言通用

## 字符串操作

### 字符串拼接

#### +号

和java一样使用+来拼接。

#### 占位符

- 基本

先{index}占位，之后再添加数据。

```c
    striWritLinng name = "张三丰";
    int age = 20;
    decimal money = 40000m;
    Console.WriteLine("我是{0}今年{1}岁工资{2}元",name,age,money);//往控制台打印内容
    Console.ReadKey();//暂停程序接收用户输入并显式到控制台在继续运行
```

- 提升

  让小数指定保留几位。

  ```c
  Console.WriteLine("{0:0.00}",n);//让n保留两位小数输出
  ```



## 转义符

和其它语言通用

\t 表示空格

## @符号

1. 取消\在字符串中的转义作用。

   ```c
   string path = @"D:\Ibat\iBAT.exe";
   ```

2. 保留文本原格式输出

   ```c
   string text = "这是一段文本
       哈哈哈";
   ```



## 三元表达式【三目运算符】

```c
int n = n < 3 ? 表达式1 : 表达式2;
//如果 n的值小于3成立那么就执行表达式1，否则执行表达式2.
```

