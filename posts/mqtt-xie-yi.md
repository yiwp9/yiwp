---
title: 'MQTT 协议'
date: 2021-09-07 11:17:20
tags: []
published: true
hideInList: false
feature: 
isTop: false
---
``` 文章图片来源于：太极创客 ```

## MQTT 协议简介

    MQTT是一个客户端服务端架构的发布/订阅模式的消息传输协议。它的设计思想是轻巧、开放、简单、规范，易于实现。这些特点使得它对很多场景来说都是很好的选择，特别是对于受限的环境如机器与机器的通信（M2M）以及物联网环境（IoT）。

    ——MQTT协议规范中文版


## 我对 MQTT 协议的阿简单理解

![图片来源于：太极创客](https://yiwp9.github.io/post-images/1631156011429.jpg)

![图片来源于：太极创客](https://yiwp9.github.io/post-images/1631156416859.jpg)

### **topic：**

云端和设备之间通信成为发布、接收消息，发布和接收消息都要通过 **topic，topic** 就相当于一个管道，一侧是发布消息的源头，另一侧是消息的接收者，如果没有这个管道（**topic**）这两端就没法通信了。

### **publish：**

**publish** 就是上面说到的消息发送者用来发送小的的工具，比如 A 为消息的发送者， A 准备给大家说一句 “你好”，就必须使用 **publish ** 来指定使用那个管道（**topic**）来发送什么消息。

### **subscribe：**

**subscribe** 与 **publish** 相对应，为消息的接收者。比如 B 想要接收某个管道（**topic**）的消息
就必须使用 **subscribe** 来订阅/绑定这个管道（**topic**），如果上面提到的 A 发送消息使用的管道（**topic**）为 messageTpoic 这个 B 使用的管道（**topic**）也为 messageTpoic，那么 B 就能收到 A 发送的 “你好”。

## 其他

MQTT 协议里还有好多其他功能，这里只简单介绍了基本的通讯，详细内容请查阅 MQTT 官方协议。