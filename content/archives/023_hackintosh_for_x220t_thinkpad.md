---
title: Hackintosh_x220t_thinkpad
---

day1

先读一读这篇教程：[国光的黑苹果安装教程 (sqlsec.com)](https://apple.sqlsec.com/)

## u盘制作

### 下载镜像

由于小黑的显卡是intel核显HD3000，所以按照教程选择Mojave 10.14。[GitHub - chris1111/Fix-Graphics-HD-3000-Mojave-10.14: Visit BLOG : https://com-chris1111.github.io](https://github.com/chris1111/Fix-Graphics-HD-3000-Mojave-10.14)。

查看其他硬件支持：[Catalina/Mojave硬件支持列表（持续更新中） | 黑果小兵的部落阁 (daliansky.net)](https://blog.daliansky.net/Mojave-Hardware-Support-List.html)

[【黑果小兵】macOS Mojave 10.14.6 18G103 正式版 with Clover 5091原版镜像双EFI双平台终极版\] | 黑果小兵的部落阁 (daliansky.net)](https://blog.daliansky.net/macOS-Mojave-10.14.6-18G87-Release-version-with-Clover-5033-original-image.html)

### 写入镜像

下载balenaEtcher。[balenaEtcher - Flash OS images to SD cards & USB drives](https://www.balena.io/etcher/)

下载diskgenius

按照教程写入镜像使用diskgenius打开。

可以看到一个EFI文件夹

文件夹下是BOOT和CLOVER

或者是BOOT和OC(opencore)

里面装有引导文件。

## 替换EFI

在互联网上找到你的机型对应的EFI文件

如果是笔记本，使用笔记基本机型加EFI、macos、hackinosh等进行搜索

黑果小兵等前辈们也有许多“普适”选择。

这里我结合前面提到的OC教程新建了一个，综合了多位大佬的ACPI文件

需要注意的坑：

* 第一是系统时间：时间会影响macos的有效期，过期的macos将不能被安装，解决办法是在终端或者bios更改时间。具体网上教程。
* 第二是机型：如果显示macos不能在此设备上安装，是因为不同的系统版本适配的机型不同，在网上可以查到系统版本的硬件支持等信息。这里使用smbios工具更改。具体参见opencore install guidance：platforminfo。这里我尝试改为iMac Pro9,1了一劳永逸。 

## 插电开机

插上u盘引导开机，将备用盘抹掉，然后装上系统。和教程一模一样。



## 特别致谢

* OC Gen-X 自动生成的 OpenCore EFI 如何完善：
  1. 添加必要的ACPI补丁 (合适的SSDT)  2. 添加GUI开机图形界面  3. 驱动集成显卡和集成声卡  4. 定制SMBIOS机型和序列号
  参考链接： https://g.ioiox.com/  
  https://dortania.github.io/OpenCore-Install-Guide/extras/big-sur
* https://github.com/daliansky/OC-little
* [国光的黑苹果安装教程 (sqlsec.com)](https://apple.sqlsec.com/2-启动盘制作/2-3.html)
* [corpnewt/GenSMBIOS: Py script that uses acidanthera's macserial to generate SMBIOS and optionally saves them to a plist. (github.com)](https://github.com/corpnewt/GenSMBIOS)
* [【黑苹果】手把手黑苹果安装教程-基于 OpenCore（持续更新中）_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1yq4y1o7cT?from=search&seid=12994242800486433620&spm_id_from=333.337.0.0)

## 回顾

![在刻录好引导盘后尝试用黑果小兵的clover直接安装](/img/image-20220107010248363.png)

![结果报了一个什么什么说我装不了的错，我也不知道什么原因](/img/image-20220107010405279.png)

于是乎继续按照教程配置opencore的文件。先是认真地读了黑果小兵的几篇文章，然后看了B站的视频教程，又在GitHub上翻了好久，主要下载了这些文件：![](/img/image-20220107010810247.png)

![一点就亮，非常愉悦：）](/img/image-20220107010836314.png)

![顺利得出其虽然已近深夜](/img/image-20220107010921481.png)

![终于出现问题了，问了群里面的大佬，又花了我快两个小时](/img/image-20220107011009229.png)

有经验的话这个问题真的超级简单，顺便感谢群里半夜回消息的老鸟

![解决了，盘是亮的不是灰蒙蒙的](/img/image-20220107011252292.png)

![自己又重启了几次](/img/image-20220107011337458.png)

![基本上成了，零点过了，我也困了](/img/image-20220107011419571.png)

![建个账户，唉嘿嘿](/img/image-20220107011512477.png)

![](/img/image-20220107011735384.png)

![明天再看有什么小问题，先睡觉](/img/image-20220107011758108.png)

-----

day2检测黑苹果的完善程度

## 1.网卡

使用USB网卡，将驱动复制在winpe系统驱动在安装，成功驱动

## 2、显卡
