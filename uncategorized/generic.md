# 泛型

在C#中T就是声明泛型类型的关键字。

当一个方法定义时不知道是为什么类型操作，那么可以声明为泛型类型。使用泛型可以避免拆装箱

## 定义泛型类型的方法

```csharp
//定义
//此方法返回值是泛型类型，参数也是泛型类型。
public static T Test<T>(T a,T b){

}

//调用
Test<string>(1,1); //这里调用明确指出是string类型，这时方法就确定了类型是什么了。
```

**示例**

```csharp
 static void Main(string[] args)
        {

            //泛型指定为string实参也要是。
            Console.WriteLine(1+Test<string>("1"));//结果11

            //泛型指定为int实参也要是。
            Console.WriteLine(1+Test<int>(1));//结果2
            Console.ReadKey();
        }

        public static T Test<T>(T n)
        {

            return n;
        }
```