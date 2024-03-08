<div align="center">
<img width="768" src="https://github.com/KPI0/AutoBuild-OpenWrt/blob/main/picture/OpenWrt.png"/>
<h1>AutoBuild-OpenWrt-Actions</h1>
</div>

#### ext4 与 squashfs 格式的区别：
- ext4 格式的 rootfs 可以扩展磁盘空间大小，而 squashfs 不能。
- squashfs 格式的 rootfs 可以使用重置功能（恢复出厂设置），而 ext4 不能。
## 安装教程
- 安装所需软件 [Rufus](https://rufus.ie/zh/) 或者 [balenaEtcher](https://etcher.balena.io/)
## 扩容教程
- 利用Ubuntu或者deepin等Linux系统扩容Overlay空间大小
- 在镜像文件后面增加空数据，比如增加10GB
- 输入命令：```dd if=/dev/zero bs=1G count=10 >> 固件.img```
- 现在执行查看分区
- 输入命令：```parted 固件.img```
- 确定需要扩容的分区号
- 输入命令：```print```
- 此时如果报错（没报错则请忽略）
Error: The backup GPT table is corrupt, but the primary appears OK, so that will be used.
OK/Cancel?  
则输入OK，敲回车。  
如果紧接着报警告（没报则请忽略）：Warning: Not all of the space available to xx.img appears to be used, you
can fix the GPT to use all of the space (an extra xx blocks) or continue with the current setting?
Fix/Ignore?  
则输入Fix，敲回车。  
- 选择正确的分区号，一般是2
- 输入命令：```resizepart 2 100%```
- 完成最后退出
- 输入指令：```quit```
- 完成扩容

# AutoBuild-OpenWrt
### 源码来自https://github.com/DHDAXCW/OpenWRT_x86_x64
