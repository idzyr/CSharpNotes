# Image

为什么是元素而不是控件，因为他单纯的显式一张图片 ，因为没有任何东西给用户与之交互。

## 支持显式的内容

### 位图

`BitmapImage`类负责处理

.jpg、.bmp、.png、.tiff、.wdp、.ico和.gif【但是gif图片不会动】

### 绘图

`DrawingImage`：这个类处理通过各种派生自绘图类的对象，表示的图像。

## 属性

- `Source` 指定图片的路径支持相对路径或绝对路径和URL网络图片。



**代码设置图片**

代码加载图片我发现可以处理的图片格式比较多相对直接从XAML设置，比如jpeg，webp，png等。

```csharp
/*———————————准备Image元素———————————————————————————————*/
            //图片路径可以是本地图片或网络图片
            string urlImage = "http://p5.qhimg.com/bdm/683_422_0/t0153f7a6e7558f8414.jpg";
            //创建uri对象，参数1 string类型路径 参数2 是相对url或绝对url或是不确定
            Uri uri = new Uri(urlImage, UriKind.Absolute);
            //创建BitmapImage对象 参数 uri对象
            BitmapImage bitmap = new BitmapImage(uri);
            Image image = new Image();  //创建Image对象
            image.Source = bitmap;  //设置要显式的图片资源 bitmap对象。

            /*+++++创建网格布局+++++++++++————————*/
            Grid grid = new Grid(); //创建Grid对象
            grid.Children.Add(image);   //添加子控件 image
            Grid.SetColumn(image, 0);   //设置image在Grid中列的位置
            Grid.SetRow(image,0);   ////设置image在Grid中行的位置
            Content = grid; //把grid布局添加到Window中。
```

