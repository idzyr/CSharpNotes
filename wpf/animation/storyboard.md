# Storyboard【故事板】

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.media.animation.storyboard?redirectedfrom=MSDN&view=netframework-4.8

一个容器时间线，该时间线为子动画提供对象和属性确定信息。一个故事板可以定义多个动画。

## 附加属性

- `TargetName` 获取或设置要进行动画处理的对象的名称。 该对象必须为 FrameworkElement、 FrameworkContentElement 或 Freezable。
- `TargetProperty` 获取或设置应进行动画处理的属性。

**控件的触发器绑定；**

```xaml
 <Button Width="80" Height="20">
            <Button.Content>
                播放动画
            </Button.Content>
            <!--设置触发器-->
            <Button.Triggers>
                <!--设置事件路由以button的单击事件为例 -->
                <EventTrigger RoutedEvent="Button.Click">
                    <!--开始一个故事板-->
                    <BeginStoryboard>
                        <!--定义故事板-->
                        <Storyboard>
                            <!--配置要改变的属性，起始值，结束值和动画持续时间-->
                            <DoubleAnimation Storyboard.TargetProperty="Height" From="20" To="50" Duration="0:0:2"/>
                            <DoubleAnimation Storyboard.TargetProperty="Width" From="80" To="200" FillBehavior="Stop" Duration="0:0:0.5"/>
                            //动画N。。。。。。
                        </Storyboard>
                    </BeginStoryboard>
                </EventTrigger>
            </Button.Triggers>
        </Button>
```

**样式触发器绑定；**

[参考EventTrigger事件触发器](#EventTrigger事件触发器)

**同步动画；**

- Timeline. FillBehavior 属性

  获取或设置一个值，该值指定 Timeline 在动画结束后的行为。

  值；HoldEnd动画结束后保持改变后的值一直等到上一个动画结束。**默认值**

  值；Stop动画结束后，自动恢复到初始值。

