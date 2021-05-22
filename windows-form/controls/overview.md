# 概览

## 通用属性

| 属性名                | 作用                                           | 值                                                   |
| --------------------- | ---------------------------------------------- | ---------------------------------------------------- |
| Name                  | 后台要获得前台的控件对象，需要使用Name属性     | string                                               |
| Text                  | 控件上显式的文本                               | string                                               |
| Anchor                | 当父控件发生改变时，以那个方向进行对齐，和拉伸 | 方位词top等                                          |
| BackColor             | 控件背景色                                     | 十六位代码                                           |
| BackgroundImage       | 控件背景图                                     | 从资源选择                                           |
| BackgroundlmageLayout | 设置图片的平铺方式                             |                                                      |
| ContextMenuStrip      | 右键菜单                                       | 需要要添加一个ContextMenuStrip控件从工具里菜单找到。 |
| Cursor                | 光标类型                                       |                                                      |
| Visible               | 设置控件是否可见                               | bool                                                 |
| Enabled               | 指示一个控件是否可用                           | bool                                                 |
| FlatStyle             | 设置控件样式                                   |                                                      |
| Font                  | 字体                                           |                                                      |
| FontColor             | 字体颜色                                       |                                                      |
| AutoSizeMode          | 设置窗口是否可以被用户修改大小                 |                                                      |



## 事件

### 注册事件

双击控件注册的都是控件默认被选中的那个事件

注册事件窗口

![1571121975268](file:///C:/Users/zyrbx/Desktop/C%23/CSharp-images/1571121975268.png)

## 常用代码

- 显式一个对话框

  ```csharp
  //显式一个对话框
              MessageBox.Show("内容","标题")
  ```

- 获取窗口工作区域大小（可以实时窗口改变后的大小）

  ```csharp
   //获取窗口工作区域的大小。
              int x = this.ClientSize.Width;
              int y = this.ClientSize.Height;
  ```

- 让控件一直在可视范围内

  ```csharp
   //获取窗口工作区域的大小。减去控件的大小就是控件可活动范围，避免控件超出窗口不可见
              //unLove是你给控件设置的Name属性的值。
              int x = this.ClientSize.Width - unLove.Width;
              int y = this.ClientSize.Height - unLove.Height;
  ```

- 修改控件的坐标

  ```csharp
  //控件的Location属性需要一个Point对象作为值。
  button.Location = new Point(x,y);
  ```