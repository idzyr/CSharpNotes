# 系统信息

## SystemParameters

包含可用来查询系统设置的属性。

> https://docs.microsoft.com/zh-cn/dotnet/api/system.windows.systemparameters?redirectedfrom=MSDN&view=netframework-4.8

**常用静态属性**

- `FullPrimaryScreenHeight` 获取主监视器上全屏窗口工作区的高度（以像素为单位）。返回值double类型
- `FullPrimaryScreenWidth` 获取主监视器上全屏窗口工作区的宽度（以像素为单位）。返回值double类型
- `WorkArea` 获取主监视器上工作区域的尺寸，不包含任务栏。
  - `WorkArea.Height` 获取高度 返回值double类型
  - `WorkArea.Width` 获取宽度返回值double类型

