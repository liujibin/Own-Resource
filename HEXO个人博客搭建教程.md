---
title: HEXO个人博客搭建教程
date: 2017-11-28 15:34:11
tags: [Hexo]
categories: HEXO搭建博客
---
<img src="/uploads/head_theme/theme1.jpg" width="100%"/>
# 前言
一直有搭建一个个人博客的想法，直到一次偶然看到大神分享的Hexo+Next+Github搭建个人博客的教程，心血来潮，搭建了一个自己的博客，圆了梦，也是新梦的启航。  
搜查了无数资料，总算搭建完成，在此分享下搭建的过程，以便自己回顾，也方便想搭建自己博客的童鞋。

<!-- more -->

# 准备
安装Hexo之前，我们首先需要安装nodejs和git。  
Nodejs：[下载地址](https://nodejs.org/en/)  
下载下来按步骤点击安装就好了，安装好之后测试下看是否安装完成，在cmd输入命令node -v，看到打印出版本号，说明nodejs安装正确  
![](/uploads/pic1.jpg)  
nodejs里面封装了npm，cmd输入命令npm -v，看到效果  
![](/uploads/pic2.jpg)  

Git：[下载地址](https://git-scm.com/)  
下载后点击安装，安装好之后，cmd输入git命令测试，看到如下效果，说明成功。   
![](/uploads/pic3.jpg)  

# 安装HEXO  
上面的准备工作做完了，我们可以安装Hexo了，cmd输入命令npm install -g hexo-cli。
安装完成后，新建一个文件夹，作为我们的站点目录，在目录下依次执行命令  
hexo init  
hexo g  
hexo s  
![](/uploads/pic4.jpg)  

现在我们就可以在浏览器输入：http://localhost:4000/就可以看到效果了。  
等等，和说好的好像不一样，并没有出现我想要的效果  
![](/uploads/pic5.jpg)  
我们查一下4000端口使用情况，发现被占用了  
![](/uploads/pic6.jpg)  
![](/uploads/pic7.jpg)  
![](/uploads/pic8.jpg)  
最后查到是被福昕阅读器的一个文档安全防护进程占用了。  
4000端口无法使用，Ctrl+c结束服务，输入命令hexo s -p 5000，切换到5000端口，启动好后，访问http://localhost:5000/，看到了效果  
![](/uploads/pic9.jpg)  

# NEXT主题  
定位到HEXO 站点目录下，执行命令git clone https://github.com/iissnan/hexo-theme-next themes/next  
![](/uploads/pic10.jpg)  
导入next主题文件  
修改站点目录下的_config.yml配置文件中的theme属性，改成next  
重新生成hexo g  
启动hexo s -p 5000  
看到next主题效果  
![](/uploads/pic11.jpg)  
到这里本地的博客雏形就出来了。