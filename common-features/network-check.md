# 检测是否联网

## ping方式

用到的类

- PIng

  > https://docs.microsoft.com/zh-cn/dotnet/api/system.net.networkinformation.ping?redirectedfrom=MSDN&view=netframework-4.8

- PingReply

  > https://docs.microsoft.com/zh-cn/dotnet/api/system.net.networkinformation.pingreply?redirectedfrom=MSDN&view=netframework-4.8

```csharp
using System.Net.NetworkInformation;       
        #region 检测网络连接状态。
        /// <summary>
        /// 通过ping指定的域名检测是否有网络连接
        /// </summary>
        /// <returns>有网络连接返回True无网络返回False</returns>
        private bool IsNetStatus()
        {
            try
            {
                //创建一个ping对象
                Ping ping = new Ping();

                //发送ping并接收ping返回状态
                /*
                 Send 方法 (String, Int32)
                 参数；
                    - String要ping的主机名（域名）
                    - Int32 等待 ICMP 回送答复消息的最大毫秒数。
                 返回值
                    PingReply 类型
                 */
                PingReply pingStatus = ping.Send("www.bilibili.com",1000);

                //判断返回内容是否有效
                /*
                  属性
                    - Status 获取ICMP 回送答复消息的状态。

                 返回值
                    - IPStatus 枚举
                        - 值
                            Success ICMP 回送请求成功（证明ping成功）
                 */

                if (pingStatus.Status == IPStatus.Success)
                {
                    //ping成功
                    return true;
                }
                else
                {
                    //ping失败
                    return false;
                }
            }
            catch 
            {
                //ping失败发生异常
                return false;
            }

        }

        #endregion
```

