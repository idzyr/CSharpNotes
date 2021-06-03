# 变换

## RenderTransform和LayoutTransform 旋转

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.uielement.rendertransform?redirectedfrom=MSDN&view=netframework-4.8#System_Windows_UIElement_RenderTransform

RenderTransform布局后在旋转控件。

LayoutTransform 旋转后在布局确立控件的坐标。

**属性**

- `Angle` 旋转角度
- `CenterX` 旋转x轴心位置
- `CenterY` 旋转y轴心位置
- `RenderTransformOrigin` 以相对坐标设置旋转轴心。

**RenderTransform；**

```xaml
<Canvas>
        <Rectangle
            Width="100" Height="100" Fill="PeachPuff" Canvas.Left="30" Canvas.Top="30">
            <Rectangle.RenderTransform>
                <RotateTransform Angle="50" CenterX="50" CenterY="50"/>
            </Rectangle.RenderTransform>
        </Rectangle>
        <!--以相对坐标配置旋转轴心-->
            <Rectangle
            Width="100" Height="100" Fill="PeachPuff" Canvas.Left="30" Canvas.Top="30" RenderTransformOrigin="0.5,0.5">
            <Rectangle.RenderTransform>
                <RotateTransform Angle="80" />
            </Rectangle.RenderTransform>
        </Rectangle>
    </Canvas>
```

**LayoutTransform ；**

```xaml
 <Grid Background="DarkViolet" Height="300" Width="200" Canvas.Left="150">
            <Rectangle Width="50" Height="50" Fill="Black">
                <Rectangle.LayoutTransform>
                    <RotateTransform Angle="50"/>
                </Rectangle.LayoutTransform>
            </Rectangle>
        </Grid>
```

## TranslateTransform【平移】

在二维 x-y 坐标系中平移（移动）对象。**使用参考旋转部分写法**

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.media.translatetransform?view=netframework-4.8

## ScaleTransform【缩放】

在 2D x-y 坐标系统内缩放对象。

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.media.scaletransform?view=netframework-4.8

## SkewTransform【倾斜】

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.media.skewtransform?view=netframework-4.8

### OpacityMask 属性逐渐透明

获取或设置不透明蒙板，作为应用于此元素已呈现内容的任何 Alpha 通道蒙板的 Brush 实现。这是一个依赖项属性。

![image-20200131140245173](transform-images/image-20200131140245173.png)

```xaml
<Canvas>
    <Rectangle Height="400" Width="300" Fill="CadetBlue"/> //底部内容
    <!-- 遮盖层/蒙版 -->
    <Button Background="White" Foreground="#FF0000" Width="298" Height="350">
        <Button.Content>点击查看全部内容</Button.Content>
        <!-- 设置蒙版属性 -->
        <Button.OpacityMask>
            <!-- 采用线性渐变刷也可以其它渐变 -->
            <LinearGradientBrush StartPoint="0,0" EndPoint="0,1">
                <!-- Transparent透明属性值 -->
                <GradientStop Color="Transparent" Offset="0"/>
                <!-- 不透明颜色 -->
                <GradientStop Color="Black" Offset="0.5"/>
            </LinearGradientBrush>
        </Button.OpacityMask>
    </Button>
</Canvas>
```

