# 字体图标

1. 作为外部文件资源引用，字体文件属性，复制到输出目录，**不要选择**不复制。生成操作选择内容。

2. `FontFamily`属性引用字体文件

   > **注意**这里的字体文件名，有时并不是字体文件名而是字体全名，如`bilifont APP"` 字体名 字体家族名

   - 第一种 `Pack://application:,,,/字体文件路径/#字体文件名"/>`
   - 第二种`/程序名;component/字体文件路径/#字体文件名不带文件后缀` 如`/FontIconDemo;component/Fonts/#bilifont`

1. XAML代码使用；

   `&#x字符对应的Unicode编码;` 如`&#xe003;`

2. c#代码使用；

   `\u字符对应的Unicode编码` 如 `\ue012`

