# ScrollViewer【滚动条】

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.controls.scrollviewer?redirectedfrom=MSDN&view=netframework-4.8

滚动条用来包裹一个容器，设置滚动条的大小，当滚动条内的控件所占空间超过滚动条大小就可以拖动滚动条了。

```xaml
<ScrollViewer Height="300"> //滚动条容器
            <StackPanel>
                <Button Height="100">1</Button>
                <Button Height="100">2</Button>
                <Button Height="100">3</Button>
                <Button Height="100">4</Button>
                <Button Height="100">5</Button>
                <Button Height="100">6</Button>
            </StackPanel>
        </ScrollViewer>
```

## 属性

- `ScrollToBottom` 垂直滚动到 ScrollViewer 内容的末尾位置。
- `ScrollToEnd` 垂直滚动到 ScrollViewer 内容的末尾位置
- `ScrollToTop` 垂直滚动到 ScrollViewer 内容的开始位置。
- `ScrollToHome` 垂直滚动到 ScrollViewer 内容的开始位置。
- `VerticalOffset` 获取一个值，该值包含滚动内容的垂直偏移量
- `ScrollableHeight` 获取一个值，该值表示可滚动的内容元素的垂直大小。
- `VerticalScrollBarVisibility` 设置垂直滚动条是否显示或隐藏。
- `HorizontalScrollBarVisibility` 设置水平滚动条是否显示或隐藏。

## 事件

`ScrollChanged` 当检测到对滚动位置、范围或视区大小进行了更改时发生



