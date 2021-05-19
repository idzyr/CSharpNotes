# 异常处理



## 异常捕获

```c#
try{
    可能会出现异常的代码
}catch{
    出现异常后处理逻辑
}

 static void Main(string[] args)
        {
            string input = null;
            try
            {
                Console.WriteLine("请输入一个数字加一");
                 input = Console.ReadLine();
                int number = Convert.ToInt32(input) + 1;
                Console.WriteLine("最终结果为{0}",number);
            }
            catch
            {
                Console.WriteLine("输入了非法字符'{0}'",input);
            }

            Console.WriteLine("按任意键退出");
            Console.ReadKey();


        }
```

