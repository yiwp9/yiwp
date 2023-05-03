---
title: 'SolidWorks 没能启动应用程序 Visual Basic，方程式和宏将不能使用。您的磁盘空间是否不足？'
date: 2021-09-10 14:42:46
tags: []
published: true
hideInList: false
feature: 
isTop: false
---
``` 本文转自 https://blog.csdn.net/weixin_39976450/article/details/99638801```
解决办法：
将C:\Program Files\Common Files\Microsoft Shared下的VBA文件夹删除即可。（不影响office正常使用）SolidWorks的初始化VBA引擎与微软office的VBA有冲突。----win7 64位
经验：office重装过，然后出现SolidWorks没能启动应用程序VISUAL BASIC的问题。 