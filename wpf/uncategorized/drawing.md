# 绘图

## 基本图形

> **提示；**
>
> 基本图形同样也可以响应事件操作

### Rectangle【矩形】

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.shapes.rectangle?redirectedfrom=MSDN&view=netframework-4.8

**属性**

- `Stroke`描边样式
- `Fill` 填充样式
- `RadiusX` 获取或设置令矩形边角改为圆角的椭圆半径( X 轴)。
- `RadiusY` 获取或设置令矩形边角改为圆角的椭圆半径(Y 轴)。

### Ellipse【椭圆】

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.shapes.ellipse?redirectedfrom=MSDN&view=netframework-4.8

### Polygon【多边形】

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.shapes.polygon?redirectedfrom=MSDN&view=netframework-4.8

自动闭合路径创建形状。

**属性**

- `Points` 设置多个坐标点，xy坐标用逗号分割，多个坐标用空格分割，如`Points="0,10 100,20 300,60 400,20"`

## 线

### Line【直线】

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.shapes.line?redirectedfrom=MSDN&view=netframework-4.8

**属性**

- `X1和Y1` 起始点坐标。
- `X2和Y2` 结束点坐标。
- `StrokeThickness` 获取或设置 Shape 边框的宽度。
- `StrokeEndLineCap` 获取或设置一个 PenLineCap 枚举值，该值描述位于直线末端的 形状。
- `StrokeStartLineCap` 获取或设置一个 PenLineCap 枚举值，该值描述位于 Stroke 起始处的 形状。
- `StrokeDashArray`设置虚线 获取或设置 Double 值的集合，这些值指示用于勾勒形状轮廓的虚线和间隙样式 虚线点之间的距离。 如`StrokeDashArray="1 2 3 4"`

### Polyline【折线】

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.shapes.polyline?redirectedfrom=MSDN&view=netframework-4.8

**属性**

- `Points` 设置多个坐标点，xy坐标用逗号分割，多个坐标用空格分割，如`Points="0,10 100,20 300,60 400,20"`

### ViewBox【控件】

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.controls.viewbox?view=netframework-4.8

定义一个内容修饰器，以便拉伸或缩放单一子项使其填满可用的控件,当窗口大小改变时里面的控件也会随之改变。

## Path路径

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.shapes.path?redirectedfrom=MSDN&view=netframework-4.8

通过路径绘制图形

**属性**

- Data 获取或设置指定要绘制的形状的 Geometry。
  - Geometry https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.media.geometry?redirectedfrom=MSDN&view=netframework-4.8

```xaml
<Path Fill="Black">
    <!--配置绘制路径-->
            <Path.Data>
                <!--//绘制矩形-->
                <RectangleGeometry Rect="10,10,100/> 
            </Path.Data>
        </Path>
```

**绘制其它形状;**

```
         System.Windows.Media.CombinedGeometry 
         System.Windows.Media.EllipseGeometry //椭圆
         System.Windows.Media.GeometryGroup //表示由其他 Geometry 对象组成的复合几何图形
         System.Windows.Media.LineGeometry //直线
         System.Windows.Media.PathGeometry //
         System.Windows.Media.RectangleGeometry //矩形
         System.Windows.Media.StreamGeometry 
```

### 路径微语言

使用少量的代码绘制复杂的图形。



## DrawingVisual 可视化对象 

DrawingVisual 是一个可视对象，可用于在屏幕上呈现向量图形。 内容由系统保存。

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.media.drawingvisual?redirectedfrom=MSDN&view=netframework-4.8

