# 音乐播放器

> WindowsMediaPlayer

## 控制

- Ctlcontrols.play();播放

- Ctlcontrols.pause();暂停

- Ctlcontrols.stop();停止

- settings.autoStart 设置是否自动播放【默认是true】

  - 注意；

    如果URL属性中有音频地址那么设置此属性会无效，解决方案是，在词属性设置后在给URL属性赋值。

- settings.mute 设置是否为静音。

- currentMedia.duration 获取总时长以秒为单位

- playerMusic.currentMedia.durationString 获取总时长以时分秒为格式 00:00

- playerMusic.Ctlcontrols.currentPosition 获取当前播放时间以秒为单位

- playerMusic.Ctlcontrols.currentPositionString 获取当前播放时间以时分秒为格式 00:00

- settings.volume 音量，0-100

## 歌词

### 歌词格式

> 五月天 - 倔强.lrc格式

```
[00:15.57]当我和世界不一样
[00:44.89]那就让我不一样
[00:47.44]坚持对我来说就是以刚克刚
[00:53.78]我如果对自己妥协
[00:56.35]如果对自己说谎
[00:59.76]即使你不原谅我也不能原谅
[01:04.23]最美的愿望一定最疯狂
[01:08.60]我就是我自己的神在我活的地方
[01:18.76]我和我最后的倔强
[01:20.63]握紧双手绝对不放
[01:23.44]下一站是不是天堂
[01:26.32]就算失望不能绝望
[01:29.31]我和我骄傲的倔强
[01:32.73]我在风中大声的唱
[01:37.07]这一次为自己疯狂
[01:40.21]就这一次我和我的倔强
[01:44.52]对爱我的人别紧张
[02:03.12]我的固执很善良
[02:06.23]我的手越肮脏眼神越是发光
[02:09.06]你不在乎我的过往
[02:13.14]看到了我的翅膀
[02:16.67]你说被火烧过才能出现凤凰
[02:23.06]逆风的方向更适合飞翔
[02:25.62]我不怕千万人阻挡只怕自己投降
[02:33.66]我和我最后的倔强
[02:37.21]握紧双手绝对不放
[02:41.93]下一站是不是天堂
[02:44.89]就算失望不能绝望
[02:47.76]我和我骄傲的倔强
[02:50.85]我在风中大声的唱
[02:54.02]这一次为自己疯狂
[02:57.04]就这一次我和我的倔强
[03:12.72]我和我最后的倔强
[03:14.26]握紧双手绝对不放
[03:18.70]下一站是不是天堂
[03:20.33]就算失望不能绝望
[03:24.70]我和我骄傲的倔强
[03:27.74]我在风中大声的唱
[03:29.40]这一次为自己疯狂
[03:32.32]就这一次我和我的倔强
[03:40.38]就这一次让我大声唱
[03:43.51]lalalala...
[03:43.77]就算失望不能绝望...
[03:54.66]lalalalala
[04:05.16]就这一次我和我的倔强
```

### 原理

1. 读取歌词文件按行读取

2. 格式化歌词

3. 去除时间中的 [ ]括号 去除其中的:冒号 得到04 05.16 两个元素分别是[0]和[1]

4. 用0元素去乘以60换算为秒再加1元素中的秒数。这样整个就转换为秒了

5. 显式歌词，条件，当前歌曲时间【获取当前播放的秒】大于或等于第N句歌词的时间并且，小于第N+句歌词时间。就播放第N句歌词【在这个时间段内显式 第N句歌词 】。

   **注意；**这里的N可以理解为第一句歌词时间，N+1可以理解为第二句歌词时间。**每秒判断一次**

    大于或等于第N句歌词的时间 = 歌词显式的入点

    小于第N+句歌词时间 = 歌词显式的出点

#### 实列代码

```csharp
                //读取歌词文件
                string[] lrcText = File.ReadAllLines("倔强.lrc",Encoding.Default);
       //存储时间
        List<double> listTime = new List<double>();
        //存储歌词
        List<string> listLrcText = new List<string>();

//格式化歌词
 for (int i = 0; i < lrcText.Length; i++)
            {
                //[00:15.57]当我和世界不一样
                string[] lrcTemp = lrcText[i].Split(new char[] { '[', ']' }, StringSplitOptions.RemoveEmptyEntries);
                //00:15.57   lrcTemp[0]
                //当我和世界不一样 lrcTemp[1]
                string[] lrcNewTemp = lrcTemp[0].Split(new char[] { ':' }, StringSplitOptions.RemoveEmptyEntries);
                //00 lrcNewTemp[0]
                //15.57 lrcNewTemp[1]
                double time = double.Parse(lrcNewTemp[0]) * 60 + double.Parse(lrcNewTemp[1]);
                //把截取出来的时间加到泛型集合中
                listTime.Add(time);
                //把这个时间所对应的歌词存储到泛型集合中
                listLrcText.Add(lrcTemp[1]);
            }
//显式歌词
 for (int i = 0; i < listTime.Count; i++)
            {
                if (musicPlayer.Ctlcontrols.currentPosition >= listTime[i] && musicPlayer.Ctlcontrols.currentPosition < listTime[i + 1])
                {
                    label2.Text = listLrcText[i];
                }
            }
```



