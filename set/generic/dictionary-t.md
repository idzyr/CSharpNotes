# Dictionary<TKey, TValue>

> https://docs.microsoft.com/zh-cn/dotnet/api/system.collections.generic.dictionary-2?redirectedfrom=MSDN&view=netframework-4.8

Hastable泛型类字典泛型

## 使用

```c
   Dictionary<int, string> dictionary = new Dictionary<int, string>();//创建一个泛型键值对集合
dictionary[0]//根据键获得元素。
```

## foreach高级遍历

```c
            Dictionary<int, string> dic = new Dictionary<int, string>();
            dic.Add(1, "张三");
            dic.Add(2, "李四");
            dic.Add(3, "王五");
            dic[1] = "新来的";//直接通过key赋值
    //KeyValuePair<int,string>遍历键值集合关键词<>中的类型要和被遍历结合一致。
    //kv 包含了键和值，所以都可以直接点出来。
    //dic 要遍历的集合。
            foreach (KeyValuePair<int,string> kv in dic)
            {
                Console.WriteLine("{0}---{1}",kv.Key,kv.Value);
                //通过，kv.Key获取键名，kv.Value获取键值。
            }
```

