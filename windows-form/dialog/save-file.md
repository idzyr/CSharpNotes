# SaveFileDialog【保存文件】

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.forms.savefiledialog?redirectedfrom=MSDN&view=netframework-4.8

SaveFileDialog

## 属性

- `Title` 获取或设置文件对话框标题。

- `InitialDirectory` 获取或设置文件对话框显示的初始目录。

- `Filter` 获取或设置当前文件名筛选器字符串，该字符串决定对话框的“另存为文件类型”或“文件类型”框中出现的选择内容。

  ```csharp
  Filter = "文本|*.txt|所有文件|*.*";
  "提示文件类型|后缀筛选"多组规则也要使用|分割。
  ```

- `FileName` 获取或设置一个包含在文件对话框中选定的文件名的字符串。

## 方法

- `ShowDialog()` 显式对话框

