---
title: Maix-II DOCK 常见问题指南

---

>这里记录 Maix-II DOCK 相关的 A&Q 常见问题。

## 没有弹出 U 盘或者 adb 提示 device not found

![adb_error](./asserts/faq/adb_error.jpg)

出现这种问题的情况有如下可能：

1. 所使用的 TypeC 线只有供电功能，没有数据传输功能
2. 使用的是 C2C 数据线
3. 板子不是通过 OTG 口与电脑连接
4. U 盘没出现，需要手动卸载 ADB 驱动
5. 板子 LINUX 系统没启动，比如没有插入烧录过系统的 TF 卡

## 虚拟 U 盘文件复制失败，看不到文件

### 从电脑复制到 U 盘

这种情况可能是文件较大没能完整传输所导致的，需要在传输结束后先在电脑上移除虚拟 U 盘，然后在板子执行 `reboot` 命令或者按下 `RST` 键重启板子来加载文件系统。

### 在 U 盘创建文件

只用板子命令行终端在 `/root/` 下创建文件够不会同步在 U 盘里显示，这时需要重启一下就能在 U 盘里看到通过板子终端在 `/root/` 所创建的文件了。

## 镜像卡插上后不显示 U 盘无反应，屏幕也不亮。

1. 确保镜像卡正常且烧录成功
2. 确保上电的就是 OTG 口，并且 M2DOCK 的电源灯正常工作。
3. 确保已安装好 MaixPy3 以及附带的驱动并删除驱动。
4. 更换线材重试，更换电脑 USB 口重试，仍然加载不出来，更换电脑确认。
5. 以上操作后还是不行请再次使用 SD Card Formatter 重新格式化 SD 卡 再次烧录上电或联系淘宝客服。

## 本地 pip 安装失败

M2DOCK 不能本地编译以及本地 pip安装，只能搭配 Maixpy3 使用。

## 使用屏幕时呈花屏状态

1. 排线是否插稳，查看是否线序被破坏，接触不良导致的。
2. fb 缓冲区是否异常导致的
3. 尝试重启板卡看看是否还会花屏
4. 硬件问题

## 如何更换屏幕及摄像头的设备树

目前开发板支持的屏幕有 1.3寸、2.4寸、2.8寸 的 IPS 屏，且只是支持在我们淘宝上售卖的显示屏；对于别的屏幕有需求的，可以走商务通道进行定制。

如何进行屏幕的切换及更新设备树：[点击查看](https://wiki.sipeed.com/hardware/zh/maixII/M2/other.html#%E5%88%87%E6%8D%A2%E5%B1%8F%E5%B9%95)

目前 MaixII-Dock 开发板目前支持的摄像头有 sp2305、vs3205、ov2685（只支持在官方店上再售卖的摄像头，有别的摄像头需求可以进行商务定制），摄像头之间的切换同样时需要更换设备树文件，更换方式上面的更换屏幕一样的。

如何进行摄像头以及设备树的切换：[点击查看](https://wiki.sipeed.com/hardware/zh/maixII/M2/other.html#%E6%9B%B4%E6%8D%A2%E6%91%84%E5%83%8F%E5%A4%B4)

## 脱机运行

对于 M2Dock，前面说过开机启动代码顺序是 `/root/app/main.py > /root/main.py` ，所以在保存的时候自己注意下保存位置。

