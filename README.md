# ARM OpenWrt 云编译

此仓库从 [openwrt-build-x86](https://github.com/licong87/openwrt-build-x86) 拆分，使用 LibWrt 25.12-nss 源码编译 IPQ60xx 固件。

在 Actions 中运行 `ipq60xx-libWrt`，工作流会分别编译：

- `nowifi-ress01`
- `nowifi-znm2`
- `wifi-ress01`

编译完成后在本仓库 Releases 下载固件。每周一北京时间 08:15 也会自动编译；Auto-Clean 按仓库自身配置清理历史记录。

构建核心和公共脚本与 x86 仓库分别维护；ARM 保留设备原有网口定义；主路由 PPPoE IPv6 和插件初始选项与 x86 对齐。软件包和 feeds 均随上游更新，实际刷机前请确认镜像对应设备并备份配置。

## ARM 主路由默认设置

首次启动（或保留配置升级后首次启动）设置 WAN IPv6 自动获取与前缀委派、LAN /64、关闭 LAN 前缀委派、RA/SLAAC、过滤 dnsmasq AAAA 查询，并停用 LAN DHCPv6 和 RA IPv6 DNS。仅停用与 WAN 绑定同一设备的默认 DHCPv6 wan6；不设置拨号账号或更改网口定义。脚本会更改已有 IPv6 配置，升级前请备份并核查；实际 IPv6 连接取决于运营商。

Nikki 默认 TUN 和 IPv6 接管，API 密码为 123456；选择配置后自行启用，勿将 API 开放至公网。ZeroTier 默认网络勾选启用、管理路由、入站、转发和伪装，网络 ID 留空、全局服务需自行启用。UPnP 和 Vlmcsd 默认开启；UPnP 使用源码支持的私有 IPv4 选项。服务包默认值对全新安装有效，保留配置升级不会覆盖现有插件配置。
