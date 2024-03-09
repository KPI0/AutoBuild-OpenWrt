<div align="center">
<img width="768" src="https://github.com/KPI0/AutoBuild-OpenWrt/blob/main/picture/OpenWrt.png"/>
<h1>AutoBuild-OpenWrt-Actions</h1>
</div>

#### ext4 与 squashfs 格式的区别：
- ext4 格式的 rootfs 可以扩展磁盘空间大小，而 squashfs 不能。
- squashfs 格式的 rootfs 可以使用重置功能（恢复出厂设置），而 ext4 不能。

## 安装教程
- 利用硬盘盒将固件烧录到硬盘里
- 安装所需软件 [Rufus](https://rufus.ie/zh/) 或者 [balenaEtcher](https://etcher.balena.io/)

## 扩容教程
#### [参考原文](https://blog.csdn.net/zengd0/article/details/124934933)
- 利用Ubuntu或者deepin等Linux系统扩容Overlay空间大小
- 把 .gz 压缩文件解压为 .img 镜像文件
- 输入命令：```gzip -kd 固件.img.gz```
- 在镜像文件后面增加空数据，比如增加10GB
- 输入命令：```dd if=/dev/zero bs=1G count=10 >> 固件.img```
- 现在执行查看分区
- 输入命令：```parted 固件.img```
- 确定需要扩容的分区号
- 输入命令：```print```
- 此时如果报错（没报错则请忽略）</br>
Error: The backup GPT table is corrupt, but the primary appears OK, so that will be used.</br>
OK/Cancel?  
- 输入命令：```OK```
- 如果紧接着报警告（没报则请忽略）</br>
Warning: Not all of the space available to xx.img appears to be used, you
can fix the GPT to use all of the space (an extra xx blocks) or continue with the current setting?</br>
Fix/Ignore?  
- 输入命令：```Fix```
- 选择正确的分区号（列表中显示最大空间的序号），一般选 2
- 输入命令：```resizepart 2 100%```
- 完成最后退出
- 输入命令：```quit```
- 完成扩容

## 插件预览
<details>
<summary><b>&nbsp; 插件预览</b></summary>
<br/>
<details>
<summary><b>├── 状态</b></summary>
　├── 概况<br/>
　├── 防火墙<br/>
　├── 路由表<br/>
　├── 系统日志<br/>
　├── 内核日志<br/>
　├── 系统进程<br/>
　├── 实时信息<br/>
　├── 实时监控<br/>
　├── WireGuard状态<br/>
　└── 负载均衡
</details>
<details>
<summary><b>├── 系统</b></summary>
　├── Web管理<br/>
　├── 系统<br/>
　├── 管理权<br/>
　├── 软件包<br/>
　├── TTYD 终端<br/>
　├── 启动项<br/>
　├── 计划任务<br/>
　├── 挂载点<br/>
　├── 磁盘管理<br/>
　├── 备份/升级<br/>
　├── 自定义命令<br/>
　├── 文件传输<br/>
　├── Argon 主题设置<br/>
　└── 重启
</details>
<details>
<summary><b>├── 服务</b></summary>
　├── PassWall<br/>
　├── PassWall2<br/>
　├── AdGuard Home<br/>
　├── ShadowSocksR Plus+<br/>
　├── 应用过滤<br/>
　├── 全能推送<br/>
　├── 上网时间控制<br/>
　├── OpenClash<br/>
　├── Lucky<br/>
　├── 动态 DNS<br/>
　├── SmartDNS<br/>
　├── MosDNS<br/>
　├── 网络唤醒<br/>
　├── Frps<br/>
　├── UPnP<br/>
　├── Frp 内网穿透<br/>
　├── KMS 服务器<br/>
　└── Nps 内网穿透
</details>
<details>
<summary><b>├── 网络存储</b></summary>
　├── 文件助手<br/>
　├── 文件浏览器<br/>
　├── NFS 管理<br/>
　├── Alist 文件列表<br/>
　├── USB 打印服务器<br/>
　├── 硬盘休眠<br/>
　├── 打印服务器<br/>
　├── 网络共享<br/>
　├── Aria2 配置<br/>
　└── FTP 服务器
</details>
<details>
<summary><b>├── VPN</b></summary>
　├── SSR MuDB 服务器<br/>
　├── IPSec VPN 服务器<br/>
　├── SoftEther VPN 服务器<br/>
　├── PPTP VPN 服务器<br/>
　├── OpenVPN 服务器<br/>
　└── ZeroTier
</details>
<details>
<summary><b>├── 网络</b></summary>
　├── 接口<br/>
　├── 无线<br/>
　├── 访客网络<br/>
　├── DHCP/DNS<br/>
　├── 主机名<br/>
　├── IP/MAC 绑定<br/>
　├── 静态路由<br/>
　├── 诊断<br/>
　├── 防火墙<br/>
　├── PCI移动网络拨号服务<br/>
　├── USB移动网络拨号服务<br/>
　├── Socat<br/>
　├── SQM QoS<br/>
　├── 网速控制<br/>
　├── Turbo ACC 网络加速<br/>
　├── 多线多拨<br/>
　└── 负载均衡
</details>
<details>
<summary><b>├── 带宽监控</b></summary>
　├── 显示<br/>
　├── 配置<br/>
　├── 备份<br/>
　└── 实时流量监测
</details>
　└── <b>退出</b>
</details>

## 插件安装
- [关机](https://github.com/sirpdboy/luci-app-poweroffdevice)
- [定时重启](https://github.com/kongfl888/luci-app-timedreboot)
- [定时设置](https://github.com/sirpdboy/luci-app-autotimeset)

# AutoBuild-OpenWrt
### 源码来自https://github.com/DHDAXCW/OpenWRT_x86_x64
