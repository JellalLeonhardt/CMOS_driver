# 注意
代码是从ELDD的源码直接改的，v2.6.35到v2.6.36-rc1间，去掉了ioctl 而是 改用了unlocked_ioctl
故而 cmos_ioctl 也发生了相应的修改
# 使用
cmos驱动和rtc驱动都是使用的0x70和0x71端口，端口冲突从而导致cmos驱动模块无法安装
## 解决
### 方案一
如果使用的内核中rtc驱动是以模块安装的，在lsmod中可以找到，则可以通过卸载模块解决
### 方案二
如果不是，则只有重新配置编译和安装内核，配置的时候，如果使用menuconfig，则在Device drivers中可以直接找到 Real Time Clock 选项，直接 `N` 关闭即可
然后编译和安装模块内核即可