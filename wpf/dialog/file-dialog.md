# OpenFileDialog 【文件对话框】

> https://docs.microsoft.com/zh-cn/dotnet/api/microsoft.win32.openfiledialog?redirectedfrom=MSDN&view=netframework-4.8

```c
OpenFileDialog fileDialog = new OpenFileDialog();
            fileDialog.Title = "打开PKG文件";
            fileDialog.CheckPathExists = true; //获取或设置一个值，该值指定如果用户键入无效的路径和文件名，是否显示警告。
            fileDialog.Multiselect = false; //是否支持多选
            fileDialog.Filter = "PKG文件|*.pkg"; //过滤文件
            //如果用户点击了确认按钮
            if ((bool)fileDialog.ShowDialog())
            {
                PKGPath.Text = fileDialog.FileName;
            }
```

