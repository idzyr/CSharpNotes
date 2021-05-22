# ArrayList

> https://docs.microsoft.com/zh-cn/dotnet/api/system.collections.arraylist?view=netframework-4.8

存储多类型数据集合

## 属性

- `Count`获取集合长度。
- `Capacity` 获取或设置 ArrayList 可包含的元素数 ,实际存储的元素大小要是超过可包含的，会自动开一倍的空间。

## 方法

- `Add()`往集合中添加单个数据。
- `AddRange()`;往集合中添加集合可以。
- `Clear()` 从 ArrayList 中移除所有元素。
- `Remove()` 从 ArrayList 中移除特定**对象**的第一个匹配项。
- `RemoveAt()` 移除 ArrayList 的指定**索引**处的元素。
- `RemoveRange()` 从 ArrayList 中移除一定**范围**的元素
- `Reverse()` 将整个 ArrayList 中元素的顺序反转。
- `Sort()` 对整个 ArrayList 中的元素进行排序。
- `Insert(indiex,value)` 将元素插入 ArrayList 的指定索引处
- `InsertRange(index,list)` 插入一个集合到 ArrayList 的指定索引处
- `Contains()` 确定某元素是否在 ArrayList 中。

## 使用

```c
ArrayList arrayList = new ArrayList();//创建集合对象。
arrayList[0];//获取索引出的值
```