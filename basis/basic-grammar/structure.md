# 结构

结构可以一次性声明多个不同类型的变量。

## 语法

```c
public struct 结构名 { 
    成员,或叫字段
}

//声明一个人的结构
public struct Person{
    ///成员不加public外部无法访问，不加作用域只在结构中。
    public string _name; //姓名
    public int _age;//年龄
    public char _gender;//性别
}
/*—————————使用这个结构—————————————*/
//创建一个结构类型的变量
Person myPerson；
//通过变量去访问里面的成员，并赋值。
myPerson._name = "张三";
```

## 声明位置

**声明到类的外面，名称空间中。结构命名规则为大驼峰，字段要以下划线来命名。**

