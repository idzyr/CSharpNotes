# ToolTip工具提示

复杂提示效果编写

```xaml
<Button Width="100" Height="22" HorizontalAlignment="Left" Content="测试按钮">
    <!-- ToolTip 属性标签开始 -->
    <Button.ToolTip>
        <ToolTip Background="#666666">
            <StackPanel>
                <TextBox Text="这是提示内容"/>
                <Image Source="http://game.gtimg.cn/images/yxzj/img201606/heroimg/199/199.jpg"/>
            </StackPanel>
        </ToolTip>
    </Button.ToolTip>
    <!-- ToolTip 属性标签结束 -->
</Button>
//这里写提示内容可以包含文字也有了图片。
```

