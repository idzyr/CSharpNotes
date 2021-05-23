# 查找桌面层句柄

> 使用win32API，通过桌面句柄可以实现动态桌面效果

**代码**

```csharp
using System;
using System.Text;
using System.Windows;
using System.Runtime.InteropServices; //调用win32必须导入空间

namespace 背景句柄
{
    //声明委托【EnumWindows回调使用】
    public delegate bool EnumWindowsProc(IntPtr hWnd, int lParam);
    /// <summary>
    /// MainWindow.xaml 的交互逻辑
    /// </summary>
    public partial class MainWindow : Window
    {
        private IntPtr desktopHandle;  //桌面层窗口句柄
        private StringBuilder className = new StringBuilder(); //窗口类名
        /*————————————————————————声明必要win32API————————————————————————————————————————————————————*/
        //遍历顶级窗口方法。//参数1 回调函数【C#用委托类型】。
        [DllImport("user32.dll")]
        private static extern int EnumWindows(EnumWindowsProc ewp, int lParam);

        //检测窗口是否可见方法
        [DllImport("user32.dll")]
        private static extern bool IsWindowVisible(IntPtr hWnd);

        //查找子窗口方法
        [DllImport("User32.dll")]
        public static extern IntPtr FindWindowEx(IntPtr hWndParent, IntPtr hWndChildAfter, String lpszClass, String lpszWindow);

        //获取类名
        [DllImport("User32.dll")]
        private static extern int GetClassName(IntPtr hWnd, StringBuilder lpClassName, int nMaxCount);
        public MainWindow()
        {
            InitializeComponent();
        }

        /*———————————————————————————————————————————————————————————*/
        public bool ADA_EnumWindowsProc(IntPtr hWnd, int lParam)
        {
            /* 判断条件 
             条件一；窗口不是隐藏的
             条件二；窗口下没有子窗口SHELLDLL_DefView
             条件三；窗口类名是WorkerW
             */

           //获取句柄对应的类名
            GetClassName(hWnd, className, 100);

            if (IsWindowVisible(hWnd) && className.ToString() == "WorkerW" && IntPtr.Zero == (FindWindowEx(hWnd, IntPtr.Zero, "SHELLDLL_DefView", null)))
            {
                desktopHandle = hWnd; //满足条件保存句柄
                return false;    
            }
            return true;
        }

        private void Btn_set_Click(object sender, RoutedEventArgs e)
        {
            //初始委托类型。
            EnumWindowsProc ewp = new EnumWindowsProc(ADA_EnumWindowsProc);
            //调用EnumWindows方法查找桌面句柄。到大最后一个顶级窗口或回调返回false停止查找
            EnumWindows(ewp, 0);    
            MessageBox.Show("找到句柄了");
        }
    }
}
```