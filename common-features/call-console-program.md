# 窗体调用控制台程序

## 接收返回值调用

**执行cmd命令；**

```csharp
Process CmdProcess = new Process(); //创建进程
CmdProcess.StartInfo.FileName = "cmd.exe"; //指定cmd程序
CmdProcess.StartInfo.CreateNoWindow = true;         // 不创建新窗口    
CmdProcess.StartInfo.UseShellExecute = false;       //不启用shell启动进程  
CmdProcess.StartInfo.RedirectStandardInput = true;  // 重定向输入    
CmdProcess.StartInfo.RedirectStandardOutput = true; // 重定向标准输出    
CmdProcess.StartInfo.RedirectStandardError = true;  // 重定向错误输出  
CmdProcess.StartInfo.Arguments = "/c " + "ping www.baidu.com"; //“/C”表示执行完命令后马上退出  
CmdProcess.Start();//开启进程

Console.WriteLine(CmdProcess.StandardOutput.ReadToEnd());//获取执行正常返回值  

CmdProcess.WaitForExit();//等待程序执行完退出进程  

CmdProcess.Close();//结束  
```



**调用第三方控制台程序；**

> 有的控制台程序输出信息都归类为**错误信息了**，在获取返回信息时要注意。



```csharp
 Process p = new System.Diagnostics.Process(); //创建一个进程
 p.StartInfo.FileName = @".\RePKG.exe"; //调用控制台程序路径
 p.StartInfo.UseShellExecute = false; //不使用操作系统shell启动
 p.StartInfo.RedirectStandardOutput = true; // 由调用程序获取输出信息
 p.StartInfo.RedirectStandardError = true;//重定向标准错误输出
 p.StartInfo.RedirectStandardInp    ut = true;//接受来自调用程序的输入信息
 p.StartInfo.CreateNoWindow = true;//不显示程序窗口
 p.StartInfo.Arguments = "version"; //调用输入命令

 p.Start(); //启动进程。

 /*————————同步接收返回信息（阻塞）—————————————————————*/
 string normalOutput = string.Empty;
 normalOutput = p.StandardOutput.ReadToEnd(); //读取正常输出信息。
 string errorOutput = p.StandardError.ReadToEnd(); //读取错误输出信息
 string result = normalOutput == "" ? errorOutput : normalOutput;
 Console.WriteLine(result);

 p.Close(); //关闭进程释放资源。
```



## 解决阻塞问题

### 超时中止调用

> 不适用UI界面程序。

```csharp
//写在p.Start();后面
p.WaitForExit(1000); //等待一段时间，系统将卡在这里一段时间。时间长度由括号内的参数决定，单位为毫秒。

if (!p.HasExited)//进程已终止，则为 true；否则为 false。 
{
    p.Kill(); //终止进程
}
//读取返回信息的后面。
```

### 异步调用

> **注意；**
>
> 不要忘记处理路径空格问题。

**方式一；**

1. 声明委托
2. 声明委托事件
3. 将相应方法注册或绑定到委托事件中
4. 实现委托类型方法，异步调用，需要invoke

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Windows.Forms;
using System.Diagnostics;
using System.IO;
namespace Test
{

    // 1.声明委托
    public delegate void DelReadStdOutput(string result); //接收标准委托
    public delegate void DelReadErrOutput(string result); //接收错误委托

    public partial class Form1 : Form
    {
        // 2.声明委托事件方法
        public event DelReadStdOutput ReadStdOutput; //读取标准输出
        public event DelReadErrOutput ReadErrOutput; //读取错误输出

        public Form1()
        {
            InitializeComponent();
            Init(); //调用初始化方法
        }

        /// <summary>
        /// 初始化方法
        /// </summary>
        private void Init()
        {
            //3.将相应方法注册或绑定到委托事件中
            ReadStdOutput += new DelReadStdOutput(ReadStdOutputAction);
            ReadErrOutput += new DelReadErrOutput(ReadErrOutputAction);
        }



        private void Go_Click(object sender, EventArgs e)
        {
            //启动进程执行相应命令,此例中以执行ping.exe为例
            RealAction("cmd.exe", Input.Text);
        }

        /// <summary>
        /// 执行命令方法
        /// </summary>
        /// <param name="StartFileName">负责执行命令的程序exe</param>
        /// <param name="StartFileArg">命令</param>
        private void RealAction(string StartFileName, string StartFileArg)
        {
            Process CmdProcess = new Process(); //创建进程
            CmdProcess.StartInfo.FileName = StartFileName;      // 负责执行命令的程序exe路径
            CmdProcess.StartInfo.Arguments = "/c " + StartFileArg; //执行命令 “/C”表示执行完命令后马上退出  

            CmdProcess.StartInfo.CreateNoWindow = true;         // 不显示cmd黑窗口
            CmdProcess.StartInfo.UseShellExecute = false;   //不启用shell启动进程  
            CmdProcess.StartInfo.RedirectStandardInput = true;  // 重定向输入
            CmdProcess.StartInfo.RedirectStandardOutput = true; // 重定向标准输出到调用者。
            CmdProcess.StartInfo.RedirectStandardError = true;  // 重定向错误输出到调用者。


            //OutputDataReceived事件每次应用程序向其重定向 StandardOutput 流中写入行时发生。
            CmdProcess.OutputDataReceived += new DataReceivedEventHandler(p_OutputDataReceived);
            //ErrorDataReceived当应用程序写入其重定向 StandardError 流中时发生
            CmdProcess.ErrorDataReceived += new DataReceivedEventHandler(p_ErrorDataReceived);

            //获取或设置在进程终止时是否应引发 Exited 事件。
            CmdProcess.EnableRaisingEvents = true;                      // 启用Exited事件
            CmdProcess.Exited += new EventHandler(CmdProcess_Exited);   // 注册进程结束事件

            CmdProcess.Start(); //启动进程

            //在应用程序的重定向 StandardOutput 流上开始进行异步读取操作。
            CmdProcess.BeginOutputReadLine();
            //在应用程序的重定向 StandardError 流上开始进行异步读取操作。
            CmdProcess.BeginErrorReadLine();

        }
        /*———————————实现委托类型方法——————————————————*/
        /// <summary>
        /// 读取标准输出实现委托方法
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void p_OutputDataReceived(object sender, DataReceivedEventArgs e)
        {
            if (e.Data != null)
            {
                // 5. 异步调用，需要invoke
                this.Invoke(ReadStdOutput, new object[] { e.Data });
            }
        }

        /// <summary>
        /// 读取错误输出实现委托方法
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void p_ErrorDataReceived(object sender, DataReceivedEventArgs e)
        {
            if (e.Data != null)
            {
                this.Invoke(ReadErrOutput, new object[] { e.Data });
            }
        }

        /*————————————实现事件委托方法—————————————————*/
        //当发生指定事件后下面方法会调用。
        private void ReadStdOutputAction(string result)
        {
            this.Log.AppendText(result + "\r\n");
        }

        private void ReadErrOutputAction(string result)
        {
            this.Log.AppendText(result + "\r\n");
        }

        private void CmdProcess_Exited(object sender, EventArgs e)
        {
            // 执行结束后触发
        }

    }// Class end.
}// Namespace end.
```

**方式二；**

- 根据标准输出写法可以改写为对错误输出处理的方法。

```csharp
private void Go_Click(object sender, EventArgs e)
        {
            /*———————1创建并配置进程——————————————————————*/
            using (Process process = new Process())
            {
                process.StartInfo.FileName = "cmd.exe"; //指定控制台类型程序
                process.StartInfo.CreateNoWindow = true;         // 不创建黑窗口    
                process.StartInfo.UseShellExecute = false;       //不通过shell启动进程  
                process.StartInfo.RedirectStandardInput = true;  // 重定向输入    
                process.StartInfo.RedirectStandardOutput = true; // 重定向标准输出到调用者    
                process.StartInfo.RedirectStandardError = true;  // 重定向错误输出到调用者  
                process.StartInfo.Arguments = "/c " + Input.Text; //“/C”表示执行完命令后马上退出  
                process.Start();//开启进程
                process.BeginOutputReadLine(); //开始异步按行读取标准输出。

                //为异步读取标准输出事件订阅委托处理方法
                process.OutputDataReceived += new DataReceivedEventHandler(process_OutputDataReceived);

            }
        }

        /*————————————2创建事件回调—————————————————*/
        /// <summary>
        /// 异步读取标准事件回调方法
        /// </summary>
        /// <param name="sender"></param>
        /// <param name="e"></param>
        private void process_OutputDataReceived(object sender, DataReceivedEventArgs e)
        {
            if (String.IsNullOrEmpty(e.Data) == false)
            {
                //AppendText方法,支持多线程下调用,
                AppendText(e.Data+"\r\n");
            }
        }

        /*—————————————解决多线程下调用问题————————————————*/

        #region 解决多线程下控件访问的问题  

        //声明委托类型
        public delegate void AppendTextCallback(string text);

       //实现委托类型方法
        public void AppendText(string text)
        {
            /*
             * InvokeRequired属性
             * 获取一个值，该值指示调用方在对控件进行方法调用时是否必须调用 Invoke 方法，因为调用方位于创建控件所在的线程以外的线程中。
               如果控件的 true 是在与调用线程不同的线程上创建的（说明您必须通过 Invoke 方法对控件进行调用）则为 Handle；
               否则为 false。 Implements

             */
            if (this.Log.InvokeRequired)
            {
                //实例化一个委托类型 参数;要调用的方法
                AppendTextCallback d = new AppendTextCallback(AppendText);
                /*
                 Invoke()
                    在拥有此控件的基础窗口句柄的线程上执行委托。
                 参数；
                    Delegate； 一个方法委托，它采用的参数的数量和类型与 args 参数中所包含的相同。

                    Object[];作为指定方法的参数传递的对象数组。 如果此方法没有参数，该参数可以是 null。
                 */
                this.Log.Invoke(d, text);
            }
            else
            {
                this.Log.AppendText(text);
            }
        }
        #endregion
```