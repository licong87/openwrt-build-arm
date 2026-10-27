# ARM OpenWrt 云编译

此仓库从 [openwrt-build](https://github.com/licong87/openwrt-build) 拆分，使用 LibWrt 25.12-nss 源码编译 IPQ60xx 固件。

在 Actions 中运行 `ipq60xx-libWrt`，工作流会分别编译：

- `nowifi-ress01`
- `nowifi-znm2`
- `wifi-ress01`

编译完成后在本仓库 Releases 下载固件。每周一北京时间 08:15 也会自动编译；Auto-Clean 按仓库自身配置清理历史记录。

构建核心和公共脚本与 x86 仓库分别维护；x86 专用网口和服务默认值不会应用于 ARM 固件。软件包和 feeds 均随上游更新，实际刷机前请确认镜像对应设备并备份配置。
