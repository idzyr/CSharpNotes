# 概览

1. WPFl和传统的Window窗体应用一样是通过两个部分类，分别是XAM表示其中一个部分类，后端的代码表示另一个类这个类派生自Window类，这两个类编译后构成了一个类。
2. XAML是一种声明新的语言，编写的标签最终会被实例为一个对应该该标签类的对象实例。

**示例；**

- `xmlns:` 带冒号表示用来声明名称空间 格式`xmlns:空间名`
- 名称空间值是以http开头的这种引用的资源不只一个而是一个程序集，里面包含有很多资源

```xaml
<Window x:Class="WpfApp1.MainWindow" //指定类 Window是常见的根元素。
        xmlns="http://schemas.microsoft.com/winfx/2006/XAML-images/presentation" //声明默认名称空间，默认名称空间可以不加空间名。

    //带前缀的名称空间。在书写元素时我们可以，使用指定带前缀名称空间下的元素，不写前缀默认使用默认名称空间下的元素。
        xmlns:x="http://schemas.microsoft.com/winfx/2006/XAML-images" //XAM名称空间微软定义主要解析我们的xmal代码
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp1" //当前项目的命名空间引用后可以声明自定义的控件类型
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800"> //定义一些窗口的属性

    </Grid>
</Window>
```

## x名称空间

常见元素

| 元素名          | 作用                                                         |
| --------------- | ------------------------------------------------------------ |
| x:Class         | 用来声明类，表示XAML文档编译后和那个命名空间下的那个部分类合并 |
| x:ClassModifier | 声明类的访问修饰符，也就是类的访问级别，默认是public所以不会有此元素，如果设置了那么后台的类的修饰符要和XAM中设置的一致否则会编译报错。 |
| x:Name          | 为控件创建一个唯一的标识 ，方便从后端操作。**它和Name属性不同之处在于它可以为没有Name属性的类设置name标识**。如把值设置为button1那么我们可以从后端代码中直接通过这个值去点对象中的属性方法等例 `button1.Width="200"//修改控件的宽度` 如果这个控件有Name属性那么其属性值也会变为x:Name中指定的值。 |
| x:FieldModifier | 声明类中字段的访问级别。                                     |

