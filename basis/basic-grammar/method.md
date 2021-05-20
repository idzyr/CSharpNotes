# 方法/函数

## 声明方法

格式和java一样。

```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Method
{
    class Program
    {
        static void Main(string[] args)
        {   //调用方法，调用本类中的方法可以省略类名。。
            //Program.Print();
            Print();
            Console.ReadKey();
        }

        //声明一个方法
        /*方法的描述信息*/
        /// <summary>
        /// 输出一段文字到控制台
        /// </summary>
        public static void Print()
        {
            Console.WriteLine("调用了这个方法");
        }
    }
}
```



## 高级参数

### out

`out`可以在方法中不使用return关键字，返回一个额外值。

1. 在方法的形参中使用out 修饰要返回的值。
2. 在方法内必须要为out 修饰的变量赋值。
3. 调用方法要先创建变量来接收方法内返回的额外值，被传递的额外值必须是被out修饰的形参。

```java
//调用方法 
            int n = 0;//这里可以不赋初值。
            TestOut(out n);
            Console.WriteLine(n);
			// 8

//定义方法 
public static void TestOut(out int n) {
    n = 8; 
}
```

**案例；**

```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace IsLogin
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("UserName;");
            string name = Console.ReadLine();
            Console.WriteLine("Password;");
            string pas = Console.ReadLine();

            string info;
            bool log = Login(name, pas, out info);

            Console.WriteLine("登录状态{0}",log);
            Console.WriteLine("登录信息{0}",info);

            Console.ReadKey();
        }

        /// <summary>
        /// 用户名和密码是否正确
        /// </summary>
        /// <param name="name">用户名</param>
        /// <param name="pws">密码</param>
        /// <param name="info">登录信息</param>
        /// <returns>登录是否成功</returns>
        public static bool Login(string name, string pws, out string info){
            if (name == "admin" || pws == "123456")
            {
                info = "登录成功";
                return true;
            }
            else if (name != "admin")
            {
                info = "用户名错误";
                return false;
            }
            else if (pws != "123456")
            {
                info = "密码错误";
                return false;
            }
            else
            {
                info = "未知错误";
                return false;
            }
        }
    }
}
```



### ref

被`ref` 修饰的形参，可以在方法中改变，外界的变量也同样会被改变。并返回，简而言之就是，让形参局部变量提升为全局变量。

```csharp
class Program
    {
        static void Main(string[] args)
        {
            int number = 500;
            Test(ref number);
            Console.WriteLine(number);
            Console.ReadKey();
        }

        public static void Test(ref int number)
        {
            number += 500;
        }
    }
```



### params

参数个数可变,必须是形参列表后的最后一个元素

```c
    class Program
    {
        static void Main(string[] args)
        {
            //int[] number = { 1, 2, 3, 4, 5, 6, 7 };
            //被params修饰的形参数组可以穿数组，也可以传递和可变参数类型一直的元素格式的数组。
            Sum(1,3,4,5,6,76);
            Console.ReadKey();
        }

        public static void Sum(params int[] number)//
        {
            int h = 0;
            foreach (int i in number)
            {
                h += i;
            }
            Console.WriteLine("总和为{0}", h);
        }
    }
```





## 方法重载

和java一样。

## 方法的递归

和Java中一样

