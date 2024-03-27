<div align="center">
<img width="768" src="https://github.com/KPI0/AutoBuild-OpenWrt/blob/main/picture/OpenWrt.png"/>
<h1>AutoBuild-OpenWrt-Actions</h1>
</div>

#### ext4 与 squashfs 格式的区别：
- ext4 格式的 rootfs 可以扩展磁盘空间大小，而 squashfs 不能。
- squashfs 格式的 rootfs 可以使用重置功能（恢复出厂设置），而 ext4 不能。

#### 默认编译
- 用户名：root
- 密码：password
- 管理IP：10.10.10.10
- LAN：eth0
- WAN：eth1

### 安装教程
- 利用硬盘盒将固件烧录到硬盘里
- 安装所需软件 [Rufus](https://rufus.ie/zh/) 或者 [balenaEtcher](https://etcher.balena.io/)

### 扩容教程
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
- 选择正确的分区号（列表中显示最大空间size的序号），一般选 2（Flags没有标识）
- 输入命令：```resizepart 2 100%```
- 完成最后退出
- 输入命令：```quit```
- 完成扩容

### 自定义设置
#### 1.修改默认管理IP
修改文件 scripts/lean.sh 中的 sed -i 's/192.168.1.1/10.10.10.10/g' package/base-files/files/bin/config_generate
#### 2.修改默认LAN绑定eth0，WAN绑定eth1 [参考原文](https://github.com/coolsnowwolf/lede/issues/11506)</br>
2.1 获取board id</br>
cat /tmp/sysinfo/board_name</br>
2.2 保存记住你的board id</br>
2.3 根据board id编写相应的设置</br>
如果 board id 有效，不是长得像default string那种字符</br>
编辑 target/linux/你的板子platform/etc/board.d/02_network</br>
添加你的板子case到文件中</br>
如果你的board id 无效，就是长得像default string那种字符</br>
编辑 package/base-files/files/etc/board.d/99-default_network</br>
将默认设置修改为你想要的样式</br>
#### 3.修改默认壁纸
修改文件 scripts/lean.sh 中的cp -f $GITHUB_WORKSPACE/picture/bg1.jpg luci-theme-argon/htdocs/luci-static/argon/img/bg1.jpg

### 插件预览
<details>
<summary><b>&nbsp; 插件预览（full版本）</b></summary>
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
　├── 定时重启<br/>
　├── 文件传输<br/>
　├── 重启<br/>
　├── Argon 主题设置<br/>
　└── 关机
</details>
<details>
<summary><b>├── 服务</b></summary>
　├── PassWall 2<br/>
　├── PassWall<br/>
　├── AdGuard Home<br/>
　├── ShadowSocksR Plus+<br/>
　├── 阿里云盘 WebDAV<br/>
　├── 应用过滤<br/>
　├── MosDNS<br/>
　├── 上网时间控制<br/>
　├── 全能推送<br/>
　├── OpenClash<br/>
　├── 动态 DNS<br/>
　├── QoS Nftables 版<br/>
　├── WiFi 计划<br/>
　├── SmartDNS<br/>
　├── 迅雷快鸟<br/>
　├── 网络唤醒<br/>
　├── Frps<br/>
　├── UU游戏加速器<br/>
　├── Tinyproxy<br/>
　├── UPnP<br/>
　├── Shairplay<br/>
　├── Frp 内网穿透<br/>
　├── KMS 服务器<br/>
　├── AirPlay 2 音频接收器<br/>
　├── udpxy<br/>
　├── Nps 内网穿透<br/>
　├── HAProxy<br/>
　└── MWAN3 分流助手
</details>
<details>
<summary><b>├── 网络存储</b></summary>
　├── 文件助手<br/>
　├── 文件浏览器<br/>
　├── NFS 管理<br/>
　├── Alist 文件列表<br/>
　├── qBittorrent<br/>
　├── PS3 NET 服务器<br/>
　├── USB 打印服务器<br/>
　├── 硬盘休眠<br/>
　├── miniDLNA<br/>
　├── FTP 服务器<br/>
　├── MJPG-streamer<br/>
　├── 网络共享<br/>
　├── 挂载 SMB 网络共享文件夹<br/>
　├── PCHiFi 数字转盘遥控<br/>
　├── Aria2 配置<br/>
　├── Transmission<br/>
　└── Rclone
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

### 自建 self-hosted runners
1.安装 ubuntu</br>
2.Install compilation dependencies</br>
```bash
   sudo apt update -y
   sudo apt install -y ack antlr3 asciidoc autoconf automake autopoint binutils bison build-essential \
   bzip2 ccache cmake cpio curl device-tree-compiler fastjar flex gawk gettext gcc-multilib g++-multilib \
   git gperf haveged help2man intltool libc6-dev-i386 libelf-dev libfuse-dev libglib2.0-dev libgmp3-dev \
   libltdl-dev libmpc-dev libmpfr-dev libncurses5-dev libncursesw5-dev libpython3-dev libreadline-dev \
   libssl-dev libtool lrzsz mkisofs msmtp ninja-build p7zip p7zip-full patch pkgconf python2.7 python3 \
   python3-pyelftools python3-setuptools qemu-utils rsync scons squashfs-tools subversion swig texinfo \
   uglifyjs upx-ucl unzip vim wget xmlto xxd zlib1g-dev
   ```
3.找到 Settings-Actions-Runners-New self-hosted runners</br>
Runner image 选择 Linux x64</br>
在ubuntu终端中输入

### 插件安装
- [定时重启](https://github.com/kongfl888/luci-app-timedreboot)
- [定时设置](https://github.com/sirpdboy/luci-app-autotimeset)

### AutoBuild-OpenWrt
### 源码来自https://github.com/DHDAXCW/OpenWRT_x86_x64
