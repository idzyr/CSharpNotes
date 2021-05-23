# HttpWeb【C#提供】

主要解释GET和POST请求，这两个钟请求都离不开**HttpWebRequest 【HTTP请求类】**和**HttpWebResponse 【HTTP响应类】**一个负责发起请求，一个负责响应服务器发会的数据。

详细参考API

>  **HttpWebRequest ** 【HTTP请求类】
>
> https://docs.microsoft.com/zh-cn/dotnet/api/system.net.httpwebrequest?view=netframework-4.8



> **HttpWebResponse ** 【HTTP响应类】
>
> https://docs.microsoft.com/zh-cn/dotnet/api/system.net.httpwebresponse?view=netframework-4.8



## GET请求

```csharp
//定义要请求的地址
 var url = "http://wallpaper.apc.360.cn/index.php?c=WallPaperAndroid&a=getAllCategories";
 //通过WebRequest初始化一个HttpWebRequest请求对象，Create为指定的url初始化HttpWebRequest对象
 HttpWebRequest httpReq = (HttpWebRequest) WebRequest.Create(url);
 /*———————————设置一些请求头信息———————————————————————————*/
 httpReq.Method = "GET"; //请求类型GET/POST等
 httpReq.ContentType = "text/html;charset=UTF-8"; //请求数据类型
 httpReq.UserAgent = null;//标识

 /*————————————发送请求并获得响应结果——————————————————————————————————————————*/
 //通过请求对象的GetResponse()方法获去服务响应返回的对象
 HttpWebResponse httpResp = (HttpWebResponse)httpReq.GetResponse();
 //通过响应对象的GetResponseStream方法获得数据响应流对象。
 Stream respStream = httpResp.GetResponseStream();
 //读取数据流内容
 //using是操作玩后自动释放资源格式写法。
 using (StreamReader reader = new StreamReader(respStream,Encoding.UTF8)) //解析为UTF-8编码
 {
     var result = reader.ReadToEnd();    //读取到末尾返回解析后的内容。
     Console.Write(result);
 }
```

## POST请求

改变请求方法参数.

更多细节以后在补充。

```csharp
httpReq.Method = "POST"; //请求类型GET/POST等
```