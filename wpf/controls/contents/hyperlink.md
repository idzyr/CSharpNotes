# Hyperlink超链接

```xaml
<TextBlock>
 	<Hyperlink  NavigateUri="https://space.bilibili.com/26012356" RequestNavigate="Hyperlink_OnClick" >
                            哔哩哔哩
	</Hyperlink>
</TextBlock>
```

![image-20221115190319703](hyperlink-images/image-20221115190319703.png)

处理连接点击；

使用外部浏览器打开连接

```c#
private void Hyperlink_OnClick(object sender, RoutedEventArgs e) {  
 	Hyperlink hl = (Hyperlink) sender;  
 	string navigateUri = hl.NavigateUri.ToString();  
 	Process.Start(new ProcessStartInfo(navigateUri));  
	e.Handled = true;  // 事件已处理停止事件继续传递
}  
```

**注意；**

网络上介绍使用`Click` 事件来处理链接的点击，但是这样做有一个问题，当我们和Page一起使用时会出现点击后不仅在浏览器中打开网页还会从程序内打开链接，此时我们可以使用``RequestNavigate`事件来代替前者。

![image-20221115192132851](hyperlink-images/image-20221115192132851.png)

**内存参考；**

> 同问题网友
>
> [Is there a way to open HyperLinks in external browser rather than in the Wpf Page?](https://social.msdn.microsoft.com/Forums/vstudio/en-US/e69011f8-3896-4e19-9ad2-2d51997b764a/is-there-a-way-to-open-hyperlinks-in-external-browser-rather-than-in-the-wpf-page?forum=wpf)
>
> 解决问题
>
> [WPF Hyperlink Open Browser](http://softwareindexing.blogspot.com/2008/12/wpf-hyperlink-open-browser.html)











