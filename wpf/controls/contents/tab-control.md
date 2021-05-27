# TabControl【选项卡】

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.controls.tabcontrol?redirectedfrom=MSDN&view=netframework-4.8

## 属性

- `TabStripPlacement` 获取或设置选项卡标题如何相对于选项卡内容进行对齐。

## TabItem【选项卡页】

### 属性

- `Header`设置选项卡名
- `IsSelected` 获取或设置一个值，该值指示**是否被选择 的TabItem。** 可以通过代码设置该属性为True那么这个选项页面就会被展示出来。

### 检测被选中的页

- 事件
  - `Selector. SelectionChanged` 事件
- 属性
  - `Selector. SelectedItem` 属性

```c
 private void TabControl_SelectionChanged(object sender, SelectionChangedEventArgs e)
        {
            TabControl tab = sender as TabControl;  //类型转换
     //获取或设置当前选择中的第一项，或者，如果选择为空，则返回 null。
            TabItem tabItem =  tab.SelectedItem as TabItem; 
            if (tabItem.Header.ToString() == "PKG信息")
            {
                Button_Click_3(null,null);  //调用隐藏日志方法
            }

        }
```

