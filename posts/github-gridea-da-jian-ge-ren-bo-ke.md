---
title: 'Github + Gridea 搭建个人博客'
date: 2021-06-22 19:09:10
tags: []
published: true
hideInList: false
feature: 
isTop: false
---
# **一、条件**
- 注册 Github [链接](https://github.com/)
- 下载安装 Gridea [链接](https://gridea.dev/)

# **二、创建 Github 仓库用于存储网页数据**

![](https://yiwp9.github.io/post-images/1624361974527.png)
![](https://yiwp9.github.io/post-images/1624362078240.png)
此处因为我已经创建过名称为 yiwp9.github.io 的库了，所以提示不可用，如果你没创建过则不会报错，直接点创建即可。

# **三、获取仓库的 token**

![](https://yiwp9.github.io/post-images/1624362992005.png)
![](https://yiwp9.github.io/post-images/1624362997739.png)
![](https://yiwp9.github.io/post-images/1624363003061.png)
![](https://yiwp9.github.io/post-images/1624363007040.png)
记住生成的 token

# **四、配置 Gridea**

![](https://yiwp9.github.io/post-images/1624363105092.png)

# **五、验证**
在浏览器中输入 仓库的名称 （我这里是 yiwp9.github.io）即可看到页面

![](https://yiwp9.github.io/post-images/1624363217273.png)



# **补充1**

## **自定义域名**

- **设置域名**

进入项目设置选项，一直往下翻，找到 Github Pages 
![](https://yiwp9.github.io/post-images/1624439171684.png)

- **获取页面 ip**
- 
  ![](https://yiwp9.github.io/post-images/1624439315737.png)

- **域名解析**

到域名商网站进行解析，此处以阿里云作演示：
![](https://yiwp9.github.io/post-images/1624439367527.png)

这样就可以通过 自定义的域名来访问站点了



# **补充2**

## **添加评论功能**

setting ->  Developer settings -> OAuth Apps  -> New OAuth Apps
![](https://yiwp9.github.io/post-images/1624540128346.png)

# **补充3**

## **删除底部的 RSS图标**

![](https://yiwp9.github.io/post-images/1624343380604.jpeg)

首先打开源文件下的 themes->notes->templates->includes 文件夹下的 footer.ejs .
删除如下代码，或更换为自己的代码。
![](https://yiwp9.github.io/post-images/1624343605661.png)

这样就完成啦，效果如下：

![](https://yiwp9.github.io/post-images/1624343707858.png)


<span id="busuanzi_container_page_pv">
  本文总阅读量<span id="busuanzi_value_page_pv"></span>次
</span>




