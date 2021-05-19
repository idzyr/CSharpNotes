# 枚举

**功能；**

规范开发，定义一种取值范围规则。

## 语法

```c
public enum 枚举名 //public 部分场景可以省略
{
    值1,
    值2,
    值3,
    .....
}

//声明一个性别枚举。    
public enum Gender
{
    男,
    女
}
//使用枚举中的值
//枚举类型 变量名 = 枚举名.值；
Gender gender = Gender.男;
```

## 声明位置

**声明到类的外面，名称空间中。枚举名命名规则为大驼峰**

## 类型转换

1. 枚举类型默认和int类型兼容可以互相转换。转换后值是从0开始递增1,每个枚举值都对应一个int数字。

   ```c
   //声明一个性别枚举。
   public enum Gender
   {
       //男, 转为int = 0
       男=2, //这样写值就会从2开始递增。
       女 转为int = 1 
       //以此类推
   }
   ```

1. 转换为String

   ```c
   Gender gender = Gender.男;
   gender.ToString();//枚举转string类型。
   ```

2. string转枚举

   ```c
   (要转的枚举)Enum.Parse(要转换的枚举类型,"要转换的字符串");
   Gender n = (Gender)Enum.Parse(typeof(Gender),"男");
   ```