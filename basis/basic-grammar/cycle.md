# 循环

```c#
while(循环条件){
    循环体
}

do{
    循环体
}while(循环条件);

for(初始化表达式;循环条件表达式;步进表达式){
    循环体
}

```



## foreach循环

遍历集合和数组使用

```c
foreach (变量类型 接收值的变量 in 遍历那个集合/数组)
{
    ……
}

foreach (var item in collection)//每次循环一次会把集合中的值赋值给item var 关键字是推测类型。
{
    ……
}
```

