# 变量&常量

## 变量

**语法；**

```c
int var = 0; //数据类型 变量名 = 值；
/*数据类型和c语言和java基本通用*/
```

### 特有数据类型

- decimal 金钱类型

```c
decimal money = 255m;//值必须加m否则类型不会改变。
```

- var 推断类型【不推荐使用】

  更具赋值来推断类型，确认类型。和js中的var一直弱类型声明变量关键字

  ```c
  var a = 'A'； //根据值确定var类型为字符类型
  var b = "字符"；//根据值确定var类型为字符串类型
  var c = true;//根据值确定var类型为布尔类型
  ```

### 两个变量交换

```c
/*不用第三个变量凑数法只适用于数字*/

    int n1 = 20;
    int n2 = 30;

    n1 = n1 - n2; //n1 = -20 n2 = 30
    n2 = n1 + n2;//n2 = 10 n1 = -20
    n1 = n2 - n1;//n1 = 30 n2 = 10

    Console.WriteLine("n1={0}；n2={1}", n1, n2);
    Console.ReadKey();

//与交换
    a ^= b;
    b ^= a;
    a ^= b;
```

### 类型转换

和java一样也分自动类型转换【隐式转换】和强制类型转换，语法和java一样。

在表达式中，把其中一个操作数提升为其它类型会使整个表达式类型提升。

**注意；**

1. 自动类型转换和强制类型转换必须满足两种类型互相兼容。
2. 兼容的使用Convert工具来转换。或int.Parse 这两个方法转换失败都会抛出异常。而TryParse就不会抛出异常。

- 语法

  ```c
  double n = Convert.toDouble(String);//把字符类串型转换为双精度浮点数。
  //Convert.toDouble()/外还有其它类型如。Convert.toString()等，带基本类型，格式以此类推
  
  int n = int.Parse("123");//其实Convert中也是调用的int.Parse提高效率可以使用此方法
  
  bool n = int.TryParse("要转换的字符串",out number【接收转换后的值变量】)
        //转换成功就把字符赋值给number并返回为true。否则返回false，number值为0
  ```





## 常量

```c
const 常量名 = 值; 
```

