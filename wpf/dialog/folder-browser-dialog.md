# FolderBrowserDialog 【文件夹对话框】

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.forms.folderbrowserdialog?redirectedfrom=MSDN&view=netframework-4.8 这里使用的是win窗体程序中的组件**,所以两个框架之间可以共用.**

```csharp
System.Windows.Forms.FolderBrowserDialog folderBrowserDialog = new System.Windows.Forms.FolderBrowserDialog();
            folderBrowserDialog.Description = "选择文件夹"; //提示文本
            if (folderBrowserDialog.ShowDialog() == System.Windows.Forms.DialogResult.OK)
            {
                string path = folderBrowserDialog.SelectedPath;
                return path;
            }
            return null;
```

