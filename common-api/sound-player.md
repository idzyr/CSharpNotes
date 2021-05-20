# SoundPlayer【播放wav音频】

> https://docs.microsoft.com/zh-cn/dotnet/api/system.media.soundplayer?redirectedfrom=MSDN&view=netframework-4.8

## 构造函数

- `SoundPlayer(String)` 初始化 SoundPlayer 类的新实例，并附加指定的 .wav 文件。

## 方法

- `Play()` 使用新线程播放 .wav 文件，如果尚未加载 .wav 文件，则先加载该文件。
- `PlayLooping()` 使用新线程循环播放 .wav 文件，如果尚未加载 .wav 文件，则先加载该文件。
- `PlaySync()` 播放 .wav 文件，如果尚未加载 .wav 文件，则先加载该文件。
- `Stop()` 如果播放正在进行，则停止播放声音。
- `SoundLocation(path)` 获取或设置要加载的 .wav 文件的文件路径或 URL。

