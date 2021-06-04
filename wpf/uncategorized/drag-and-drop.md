# 拖放

#### 参考

- 文章参考

  https://www.cnblogs.com/mqxs/p/7534730.html

- 事件

  - `PreviewDragOver`

    https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.uielement.previewdragover?view=netframework-4.8

  - `PreviewDrop`

    https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.uielement.previewdrop?view=netframework-4.8

- 类

  - `DragEventArgs` 包含与所有拖放事件（ DragEnter、 DragLeave、 DragOver 和 Drop）相关的参数。

    https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.drageventargs?redirectedfrom=MSDN&view=netframework-4.8

```c
 /// <summary>
        /// 拖放开始
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void TextBox_PreviewDragOver(object sender, DragEventArgs e)
        {
            // 获取或设置目标拖放操作
            //DragDropEffects枚举值 指定拖放操作的效果。
            e.Effects = DragDropEffects.Link;
            //获取或设置一个值，该值指示路由事件在路由过程中的事件处理当前状态。true表示已处理
            e.Handled = true;//必须加
        }

        /// <summary>
        /// 拖放结束
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void TextBox_PreviewDrop(object sender, DragEventArgs e)
        {
            TextBox textBox = sender as TextBox;
            //GetData(Type)方法 检索指定格式的数据对象；数据格式由 Type 对象指定。 
            //DataFormats 提供一组预定义数据格式名，可用于标识剪贴板或拖放操作中可用的数据格式。
            string[] data = (string[])e.Data.GetData(DataFormats.FileDrop); 
            //检查数据
            if (data == null || data.Length < 1 || !data[0].ToLower().EndsWith(".txt"))
            {
                textBox.Text = data[0];
            }
        }
```

