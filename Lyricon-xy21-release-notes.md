基于 TTXXXY/lyricon，保留超级岛回调、时钟切换和横竖屏行为，合并 tomakino/lyricon master 至 c93da0eef8b7aee015d2670b48e9e262fcf72cd1。

- 无超级岛时继续填满摄像头左侧可用空间，歌词右边缘额外向左 3 个物理像素。
- 有超级岛时沿用 fork 限宽，歌词右边缘向右 2 个物理像素。
- 默认在播放且歌词可见时隐藏 clock 和 notification_icon_area；保留非空自定义规则。
- 保留真正翻译优先于 SuperLyric secondary 罗马音的修复，以及 LSPosed API 102。
- 移植至上游的新歌词渲染、AI、logo 和手势功能，迁移旧样式偏好，转换旧隐藏规则数值。

[下载 release APK](https://github.com/MashiroQiu/MashiroQiu/raw/refs/heads/lyricon-apk-test-20261010/Lyricon-1.0.40-xy21-api102-release.apk)

[完整源码 ZIP](https://github.com/MashiroQiu/MashiroQiu/raw/refs/heads/lyricon-apk-test-20261010/Lyricon-xy21-upstream-source.zip)

[完整 Git 历史 bundle](https://github.com/MashiroQiu/MashiroQiu/raw/refs/heads/lyricon-apk-test-20261010/Lyricon-xy21-upstream-history.bundle)

[基于上游 c93da0e 的修改补丁](https://github.com/MashiroQiu/MashiroQiu/raw/refs/heads/lyricon-apk-test-20261010/Lyricon-xy21-on-upstream.patch)

版本 54 / 1.0.40.rc-xy21-api102，最低 Android 10。采用经过 R8 与资源缩减的 release 构建，不可调试；沿用已测试 APK 的测试签名以允许覆盖升级，不是上游官方签名。安装后打开应用一次迁移设置，再重启。

本环境没有小米真机，合并后的运行效果仍需设备确认。GitHub 连接当前不能创建 fork，源码 ZIP 和补丁先随本次构建提供。

验证：release 构建成功；22 个渲染/翻译测试全部通过；CameraWidth 的 5 个固定用例和 10000 个边界用例通过；v2 签名与上一测试版相同；最终 DEX 包含现代入口与 MiuiIslandHooker，不包含 legacy 入口或打包的宿主 API 类。源码合并提交：526c5bcbd26a2d560ae45d8fa21265a467342774。

APK SHA-256：`7d3f4cdee084d32845e1805ccc7a0da7bc2b4c7cadbf27195a213364db9d50b0`
