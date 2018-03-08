---
title: HEXO个人博客主题配置
date: 2017-11-29 16:21:46
tags: [Hexo]
categories: HEXO搭建博客
---
<img src="/uploads/head_theme/theme2.jpg" width="100%"/>
# 前言
上一篇我们介绍了个人博客的搭建，考虑到篇幅太长不利于阅读，所以上一篇只完成了本地博客的搭建。本文将会介绍如何将本地博客同步到github以及绑定自己的域名，还会涉及一些基础配置、主题的修改、以及接入第三方的一些工具。

<!-- more -->

# 准备
首先需要注册一个Github的账号，注册过程这里不多说，然后创建一个Repository，并且命名：你的Github的名字.github.io ，这里名字很重要不能乱取，要严格按照要求来。  
创建好Github的Repository之后，我们打开cmd命令工具，ping 你的Github的名字.github.io，这样我们就可以得到对应的IP地址。注册一个自己的域名，这里我是在阿里云上注册购买的域名，以自己名字命名的，结尾优先使用.com或者.cn，如果被注册了再使用其他的，看个人喜好吧。然后在阿里云控制台里面配置域名解析到我们刚刚ping出的IP地址。  
打开阿里云域名解析列表，如下图：
![](/uploads/pic14.png)
点击需要解析的域名后面对应的“解析设置”按钮，进入解析页面，点击添加解析按钮，添加对应的数据，如图：
![](/uploads/pic15.png)
到这里，我们就将域名和我们的Repository绑定了，接下来只需要将本地博客同步到Repository就可以通过域名访问了。  
### 同步到Github：  
找到之前创建的站点目录下，用git命令clone之前新建的仓库到本地，命令：  
git clone https://github.com/你的github名字/你的github名字.github.io .deploy/你的github名字.github.io    
然后在HEXO站点目录下创建一个deploy.txt文档，写入命令：  
hexo generate  
xcopy  public /s .deploy/你的github名字.github.io  
cd .deploy/你的github名字.github.io  
git add .  
git commit -m "update"  
git push origin master    
然后将扩展名改为sh，就变成一个同步代码的脚本deploy.sh。双击这个文件，然后按要求输入Github的用户名和密码就可以了（这是windows下的命令，linux下自己稍作修改）。然后我们直接输入域名就可以访问我们的博客了。  
# 站点主题配置：
爱美之心人皆有之，下面我们将介绍一下如何将我们的博客修改得更酷一点。我们这里主要使用的是NEXT模板关于NEXT可以到[NEXT主题](http://theme-next.iissnan.com/theme-settings.html)了解更多。  
在站点目录下，执行git命令，加载next模板代码到本地。  
git clone https://github.com/iissnan/hexo-theme-next themes/next    
### 站点配置：
找到站点目录下的_config.yml文件，打开（这里推荐使用MarkdownPad作为编辑工具[MarkdownPad](http://markdownpad.com/)），设置站点的标题、作者、语言等。  
```
# Site
title: Hexo博客      
subtitle: 新的开始   
description: blog.fens.me   
author: bsspirit  
email: bsspirit@gmail.com  
language: zh-Hans  
```
设置了中文需要将language设置成zh-Hans，具体语言表请看官网NEXT主题。有的发现设置了中文language，填写的中文是乱码，这是文件编码格式不对，将文件另存为UTF-8格式，覆盖原来的，就可以了。
### 主题配置：
找到HEXO站点目录下的themes目录下next目录下的_config.yml主题配置文件，找到并修改修改scheme属性，选择自己喜欢的外观，这里我选择Mist主题。  
![](/uploads/pic16.png)  
![](/uploads/pic13.png)  
在主题配置文件里面找到avatar配置，这里是设置头像的，配置好头像地址就好了。  
![](/uploads/pic17.png)   
![](/uploads/pic18.png)   
在主题配置文件里面，找到menu设置，选择需要的menu放出来：    
![](/uploads/pic19.png)   
![](/uploads/pic20.png)   
原来默认有首页和归档两个标签，这里我放出了分类和关于两个标签，需要创建对应的index页面。  
分类页面：在站点目录下执行命令  
<pre>
hexo new page categories
</pre>
关于页面：在站点目录下执行命令  
<pre>
hexo new page categories  
</pre>  
### 站点底部配置：
找到\themes\next\layout\_partials下的footer.swig文件，找到
<pre>
theme.footer.powered
</pre>
<pre>
theme.footer.powered and theme.footer.theme.enable
</pre>
<pre>
theme.footer.theme.enable
</pre>
下的内容，可以对底部展示文字格式做调整，在\themes\next\languages文件夹下的zh-Hans.yml中找到footer关键字，可以对展示内容做修改。  
<pre><code>
footer:  
  powered: "怠惰是贫穷的制造厂"  
  theme: Never say die.  
</code></pre>    

### 社交链接配置：
在主题配置文件中找到social配置，选择自己需要的站点配置链接。  
<img src="/uploads/pic21.png" />   
# 第三方功能接入：  
### 评论系统：
这里使用的gitment评论，点开链接gitment注册，  Authorization callback URL填写自己的网站链接，记下Client ID和Client Secret。在主题配置文件中找到Gitment配置  
<pre><code>
gitment:  
  enable: true  
  mint: true # RECOMMEND, A mint on Gitment, to support count, language and proxy_gateway  
  count: true # Show comments count in post meta area  
  lazy: false # Comments lazy loading with a button  
  cleanly: true # Hide 'Powered by ...' on footer, and more  
  language: zh-Hans # Force language, or auto switch by theme  
  github_user: # MUST HAVE, Your Github ID  
  github_repo: # MUST HAVE, The repo you use to store Gitment comments  
  client_id: # MUST HAVE, Github client id for the Gitment  
  client_secret: # EITHER this or proxy_gateway, Github access secret token for the Gitment  
  proxy_gateway: # Address of api proxy, See: https://github.com/aimingoo/intersect  
  redirect_protocol: # Protocol of redirect_uri with force_redirect_protocol when mint enabled 
</code></pre>  
对应的都填上就好了。  
在languages目录下en.yml中添加：
<pre><code>
gitmentbutton: Show comments from Gitment  
</code></pre>  
在zh-Hans.yml里面添加：
<pre><code>
gitmentbutton: 显示 Gitment 评论  
</code></pre>
在layout/_partials/comments.swig中找到  
<img src="/uploads/pic24.png" />  
在下面再加一个分支  
<img src="/uploads/pic22.png" />  
在layout/_third-party/comments/目录下中添加文件gitment.swig（这里代码比较多，直接放链接下载文件<a href="/uploads/gitment.swig">gitment.swig</a>）。<br />  
然后在主题下layout/_third-party/comments/index.swig文件中引入上面的文件：  
<img src="/uploads/pic23.png" />  
在source/css/_common/components/third-party/目录下添加gitment.styl文件，设置button的样式：   
<pre><code>
#gitment-display-button{  
     display: inline-block;  
     padding: 0 15px;  
     color: #0a9caf;  
     cursor: pointer;  
     font-size: 14px;  
     border: 1px solid #0a9caf;  
     border-radius: 4px;  
 }  
 #gitment-display-button:hover{  
     color: #fff;  
     background: #0a9caf;  
 } 
</code></pre>  

在source/css/_common/components/third-party/third-party.styl文件中引入相应的CSS样式即可:  
>@import "gitment";  

这样就可以了。

文末添加结束语：
在路径 \themes\next\layout_macro 中新建 passage-end-tag.swig 文件,并添加以下内容： 
![](/uploads/pic31.png)   
接着打开\themes\next\layout_macro\post.swig文件，在post-body 之后， post-footer之前添加如下画红色部分代码（post-footer之前两个DIV）：如下大概在360行左右的位置：  
![](/uploads/pic25.png)   
![](/uploads/pic26.png)   
最后在主题配置文件末尾添加：   
![](/uploads/pic27.png)   
底部显示访问量：   
打开\themes\next\layout_partials\footer.swig文件,在copyright前加上画红线这话：  
![](/uploads/pic28.png)   
然后再合适的位置添加显示统计的代码(位置还是上述这个文件)，如图：  
![](/uploads/pic29.png)   
![](/uploads/pic30.png)   

到这里就结束了。

添加百度统计，阅读次数都可以在官网看到[百度统计](http://theme-next.iissnan.com/third-party-services.html#analytics-system)，这里不多说了。  
  
本文在参考一些技术文章的基础上实践过，整理了相关流程，感谢相关分享的作者，这里附链接：  
[hexo next主题集成gitment评论系统](http://blog.csdn.net/yanzi1225627/article/details/77890414)  
[Hexo个人免费博客(三) next主题、评论、阅读量统计和站内搜索](http://blog.csdn.net/linshuhe1/article/details/52424573)  
[hexo之next主题个性化配置详细教程](http://blog.csdn.net/w_ngzeqi/article/details/73863543)  
[搭建个人博客](https://mp.weixin.qq.com/s/EUyO-7ESonfSQpD5GcCiQw)  
