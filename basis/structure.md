# 工程结构

## VS目录结构

### 总结构

VS是按照一个解决方案下面有多个小项目来组成的。

```
解决方案
    └─项目1
    └—项目2
    └—……
```

### 项目结构

```
项目
    └─Properties
    ├─引用
    ├─App.config
    ├─Program.cs【C#源码类文件】
```

**Program.cs**

```c
/*——————————引用命名空间——————————————————————*/
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;


namespace ConsoleApplication1 //项目名或命名空间
{//项目闭包
    class Program //类名
    {
        /*—————————主方法———————————————————————*/
        static void Main(string[] args)
        {
        }
    }
}
```

### 解决方案文件夹

> **提示；**
>
> 部分目录不会展示在VS中。

```
 解决方案
    |-- 项目
    |   |-- App.config
    |   |-- ConsoleApplication1.csproj【项目文件】
    |   |-- Program.cs【类文件源码】
    |   |-- Properties
    |   |   `-- AssemblyInfo.cs
    |   |-- bin
    |   |   `-- Debug
    |   |       |-- ConsoleApplication1.exe.config
    |   |       |-- ConsoleApplication1.vshost.exe
    |   |       |-- ConsoleApplication1.vshost.exe.config
    |   |       `-- ConsoleApplication1.vshost.exe.manifest
    |   `-- obj
    |       `-- Debug
    |           |-- ConsoleApplication1.csproj.FileListAbsolute.txt
    |           |-- DesignTimeResolveAssemblyReferencesInput.cache
    |           |-- TempPE
    |           |-- TemporaryGeneratedFile_036C0B5B-1481-4323-8D20-8F5ADCB23D92.cs
    |           |-- TemporaryGeneratedFile_5937a670-0e60-4077-877b-f7221da3dda1.cs
    |           `-- TemporaryGeneratedFile_E7A71F73-0F8D-4B9B-B56E-8E70B10BC5D3.cs
    |-- ConsoleApplication1.sln【解决方案文件存储这方案信息】
    `-- ConsoleApplication1.v12.suo【隐藏文件不要修改】
```

