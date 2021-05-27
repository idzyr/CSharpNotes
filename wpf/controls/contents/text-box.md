# TextBox【文本框】

## 属性

- `TextWrapping` 文本是否换行
- `AcceptsReturn` 多行显式。
- `HorizontalScrollBarVisibility` 获取或设置一个值，该值指示是否显示水平滚动条。
- `VerticalScrollBarVisibility` 获取或设置一个值，该值指示是否显示垂直滚动条。

## 带提示文本

```xaml
 <!-- 提示文本 -->
<VisualBrush x:Key="HintText" TileMode="None" Opacity="0.5" Stretch="None" AlignmentX="Left">
    <VisualBrush.Visual>
        <TextBlock Text="可以把PKG拖拽到这里" Foreground="Black" Opacity="0.8"/>
    </VisualBrush.Visual>
</VisualBrush>
<SolidColorBrush x:Key="TextBox.Static.Border" Color="#FFABAdB3"/>
<SolidColorBrush x:Key="TextBox.MouseOver.Border" Color="#FF7EB4EA"/>
<SolidColorBrush x:Key="TextBox.Focus.Border" Color="#FF569DE5"/>
<Style x:Key="TextBoxStyle1" TargetType="{x:Type TextBox}">
    <Setter Property="Background" Value="{DynamicResource {x:Static SystemColors.WindowBrushKey}}"/>
    <Setter Property="BorderBrush" Value="{StaticResource TextBox.Static.Border}"/>
    <Setter Property="Foreground" Value="{DynamicResource {x:Static SystemColors.ControlTextBrushKey}}"/>
    <Setter Property="BorderThickness" Value="1"/>
    <Setter Property="KeyboardNavigation.TabNavigation" Value="None"/>
    <Setter Property="HorizontalContentAlignment" Value="Left"/>
    <Setter Property="FocusVisualStyle" Value="{x:Null}"/>
    <Setter Property="AllowDrop" Value="true"/>
    <Setter Property="ScrollViewer.PanningMode" Value="VerticalFirst"/>
        <Setter Property="Stylus.IsFlicksEnabled" Value="False"/>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="{x:Type TextBox}">
                    <Border x:Name="border" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Background="{TemplateBinding Background}" SnapsToDevicePixels="True">
                        <ScrollViewer x:Name="PART_ContentHost" Focusable="false" HorizontalScrollBarVisibility="Hidden" VerticalScrollBarVisibility="Hidden"/>
                    </Border>
                    <ControlTemplate.Triggers>
                        <Trigger Property="IsEnabled" Value="false">
                            <Setter Property="Opacity" TargetName="border" Value="0.56"/>
                        </Trigger>
                        <Trigger Property="IsMouseOver" Value="true">
                            <Setter Property="BorderBrush" TargetName="border" Value="{StaticResource TextBox.MouseOver.Border}"/>
                        </Trigger>
                        <Trigger Property="IsKeyboardFocused" Value="true">
                            <Setter Property="BorderBrush" TargetName="border" Value="{StaticResource TextBox.Focus.Border}"/>
                        </Trigger>
                        <MultiTrigger>
                            <MultiTrigger.Conditions>
                                <Condition Property="IsFocused" Value="False"/>
                                <Condition Property="Text" Value=""/>
                            </MultiTrigger.Conditions>
                            <MultiTrigger.Setters>
                                <Setter Property="Background" TargetName="PART_ContentHost" Value="{StaticResource HintText}"/>
                            </MultiTrigger.Setters>
                        </MultiTrigger>
                    </ControlTemplate.Triggers>
                </ControlTemplate>
            </Setter.Value>
            </Setter>
            <Style.Triggers>
                <MultiTrigger>
                    <MultiTrigger.Conditions>
                        <Condition Property="IsInactiveSelectionHighlightEnabled" Value="true"/>
                        <Condition Property="IsSelectionActive" Value="false"/>
                    </MultiTrigger.Conditions>
                    <Setter Property="SelectionBrush" Value="{DynamicResource {x:Static SystemColors.InactiveSelectionHighlightBrushKey}}"/>
                </MultiTrigger>
            </Style.Triggers>
        </Style>
```