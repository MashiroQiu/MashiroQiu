本次修复 Lyricon 播放器图标不同步/消失，以及 SuperLyric QQ 音乐时间线与播放器切换恢复问题。

- Lyricon：播放器包名改变时独立刷新 App 图标，不再依赖 providerLogo 变化；重新挂载时刷新 App 图标；提供方图标解码失败后允许重新挂载重试。
- SuperLyric：QQ 音乐解析使用完整时间线识别毫秒时间戳，拒绝把行号或固定时长当作开始时间，并区分开始/结束/时长字段。停止和切歌丢弃旧歌词；同曲目停止后允许重新解析。暂停时不外推播放时间，并采用 PlaybackState 的实际时间戳。
- 桥接层：暂时停止/未就绪后保留完整歌曲缓存，恢复播放时补回；旧 MediaController 延迟回调不再影响当前播放器。
- 保留上次的摄像头宽度、无岛左移 3px、有岛右移 2px、默认隐藏 clock/notification_icon_area、翻译优先级和 API 102 修改。

[下载 Lyricon release APK](https://github.com/MashiroQiu/MashiroQiu/raw/refs/heads/lyricon-apk-test-20261010/Lyricon-1.0.40-iconfix-release.apk)

[下载 SuperLyric release APK](https://github.com/MashiroQiu/MashiroQiu/raw/refs/heads/lyricon-apk-test-20261010/SuperLyric-4.0-qqfix-release.apk)

[Lyricon 对应源码](https://github.com/MashiroQiu/MashiroQiu/raw/refs/heads/lyricon-apk-test-20261010/Lyricon-iconfix-source.zip) · [SuperLyric 对应源码](https://github.com/MashiroQiu/MashiroQiu/raw/refs/heads/lyricon-apk-test-20261010/SuperLyric-qqfix-source.zip)

11 项针对性回归测试通过（4 项图标生命周期、4 项 QQ 时间字段、3 项播放时钟）。两个 APK 沿用之前测试包的签名，可覆盖升级。两个都安装后重启手机，让 QQ 音乐、SystemUI 和系统服务加载新代码。

本环境没有连接小米手机或 QQ 音乐实例；这里验证的是代码中可复现的错误路径，偶发症状是否完全消失仍需要真机测试。重点验证 QQ 音乐冷启动、播放器来回切换、暂停恢复和换歌。

源码提交：Lyricon `2af7a07`；SuperLyric `87cdeea`。
