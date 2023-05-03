---
title: 'win10 网络状态变成一条虚线的解决方法'
date: 2021-08-09 09:47:46
tags: []
published: true
hideInList: false
feature: 
isTop: false
---
```本文参考：https://blog.csdn.net/qq_41489527/article/details/109502016```

<!-- more -->
# 现象如下：
![](https://yiwp9.github.io/post-images/1628473899433.png)

# 解决方法
## 方法一
1.用Win+R键打开运行窗口，输入 services.msc 然后回车。
2.在服务窗口中找到 Network Location Awareness
3.双击 Network Location Awareness 服务，在常规界面点击启动类型后面的选项框中选择自动，选好后点击应用，应用自动启动后，点击服务状态下面的“启动”按钮，等待启动完成就好了。

## 方法二
1.用Win+R键打开运行窗口，输入 cmd 然后回车。
2.在弹出的黑色背景的窗口中输入 “netsh winsock reset” 再按回车键。
3.之后重启电脑

## 方法三
打开 “网络和Internet”设置” ，然后在最下面有一个“网络重置”选项，点击之后按照要求操作，然后重启电脑。
![](https://yiwp9.github.io/post-images/1628474129277.png)

## 方法四
1.用Win+R键打开运行窗口，输入 services.msc 然后回车。
2.在服务窗口，找到 Window Event log ，并点击“启动”运行。
3.如果出现报错以及无法启动的情况，说明的确是这里出现了问题，可以继续下面的操作进行修复。
4.用Win+R键打开运行窗口，输入 regedit 然后回车，打开注册表。
5.然后按照如下图片中的路径，找到 Window Event log 下面的项。（路径为：计算机\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\EventLog）
6.注意！如果之前Window Event log 不能够正常启动的话，注册表里Window Event log下面的项中，是缺少了一个“Parameters” 即没有完整如上图所示的“”“Parameters”项，缺少了里面的东西。
7.接下来的解决的办法是，要自己补全缺少的 “Parameters” 。一个是可以自己手动敲打添加，具体的名称和格式如下图结合上图所示。一个一个对照手动打进去就可以了。

8.还有一个解决办法就是，找到一个正确的注册表文件，然后重新加载一下就可以了。把正确的Window Event log注册表文件复制到桌面上，然后点击加载就可以了。
正确注册表文件链接：https://1drv.ms/u/s!Aq6lNqlSTtDHqWkD1gnhShGlLu-i?e=NPnRCG
或者新建一个文本文件，复制如下代码，再将此文件修改后缀为 reg，最后双击运行即可。
   ` Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\EventLog\Parameters]
    "ServiceDLL"=hex(2):25,00,53,00,79,00,73,00,74,00,65,00,6d,00,52,00,6f,00,6f,\
    00,74,00,25,00,5c,00,53,00,79,00,73,00,74,00,65,00,6d,00,33,00,32,00,5c,00,\
    77,00,65,00,76,00,74,00,73,00,76,00,63,00,2e,00,64,00,6c,00,6c,00,00,00
    "ServiceDllUnloadOnStop"=dword:00000001
    "ServiceMain"="ServiceMain"`