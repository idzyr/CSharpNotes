# Hastable

> https://docs.microsoft.com/zh-cn/dotnet/api/system.collections.hashtable?redirectedfrom=MSDN&view=netframework-4.8

以键值对形式存放数据

## 属性

- `Count` 获取包含在 Hashtable 中的键/值对的数目
- `Keys`获取集合中的所有key，返回一个集合。

## 方法

- `Add(key,value)` 将带有指定键和值的元素添加到 Hashtable 中。
- `Clear()` 从 Hashtable 中移除所有元素。
- `Contains(key)` 确定 Hashtable 是否包含特定键。
- `Contains(key)` 确定 Hashtable 是否包含特定键
- `ContainsValue(value)` 确定 Hashtable 是否包含特定值。
- `Remove(key)` 从 Hashtable 中移除带有指定键的元素

## 使用

```c
Hastable hastable = new Hastable();//创建键值对集合。
arrayList[key];//获取key出的值
```