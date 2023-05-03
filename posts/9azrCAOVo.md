---
title: 'MicroPython固件烧录'
date: 2022-04-25 11:04:02
tags: []
published: true
hideInList: false
feature: 
isTop: false
---

一、 固件下载
下载网站：https://micropython.org/download/
找到ESP8266
选择相应版本随便下载一个即可

二、使用软件烧录
使用 flash_download_tool_3.9.2_0 进行烧录固件，烧录成功了，但是最后一直没法正常运行。串口不停地往外发数据，而且全是乱码，同时ESP8266板载LED快速闪烁（没截图，只能描述一下）。此方案本人烧录固件后无法使用，因此放弃。

三、使用命令烧录
在使用乐鑫官方的烧录工具烧录不成功之后，按照 microPython 官方的介绍，采用命令进行烧录固件，最终成功运行了，步骤如下：

①打开命令提示符并输入：
pip install esptool

②安装成功后查看esptool版本，在命令提示符中输入：
esptool version

③擦除芯片，命令窗输入：

esptool --port +你的串口号 erase_flash
如：
esptool --port COM6 erase_flash

④开始烧录固件，命令窗输入：

esptool --port+你的端口号 --baud +波特率 write_flash --flash_size=detect 0 固件路径
如：
esptool --port COM6 --baud 460800 write_flash --flash_size=detect 0 E:\masterLif\6-embedded_workspace\microPython\esp8266-1m-20220117-v1.18.bin

⑤至此固件烧录已完成，连接esp8266测试下：

四、下载代码试试  


