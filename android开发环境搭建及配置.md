---
title: android开发环境搭建及配置
date: 2018-02-27 14:43:40
tags: [基础知识,开发环境和配置]
categories: android
---
<img src="https://i.imgur.com/cQyeK8i.jpg" width="100%"/>
## 前言
### 学而不思则罔，思而不学则殆。   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  ————孔子  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;每次学习知识都有种茫然无措、丢三落四的感觉，看到那么多的大牛整理的技术栈，我觉得是很有帮助的。从这篇文章开始整理自己的知识体系，以后学习起来有方向有目标，也方便回顾、方便把知识串联起来。加油ヾ(◍°∇°◍)ﾉﾞ！
<!--more-->
## 一、准备工作  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这里我们使用的开发工具选择android studio，首先我们需要下载好JDK和android studio，下载地址如下：  
JDK：[http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
android studio：[http://www.android-studio.org/](http://www.android-studio.org/)  
### 1、JDK下载  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;点击上面的JDK下载地址，进入oracle网站，在①处选中同意条款，然后根据对应的系统，选在下载哪个jdk。
![](https://i.imgur.com/d56zIeC.png)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;下载完成后双击应用程序安装。  
![](https://i.imgur.com/9JO3uCH.png)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;点“下一步”  
![](https://i.imgur.com/MZGZQUA.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;配置安装路径，点击“下一步”  
![](https://i.imgur.com/9uRa7M2.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;然后等待安装完成就可以了，到这里，JDK我们就安装完成了。  
### 2、配置环境变量  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;鼠标右击桌面上的“计算机”，点击“属性”，进入如下界面，然后点击“高级系统设置”。  
![](https://i.imgur.com/2xLM2ca.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;点击“环境变量”。  
![](https://i.imgur.com/VgoY3uF.png)  
在“系统环境变量”里面找到如下三个环境变量，加入对应的值；如果找不到环境变量，就新建一个。 
>|变量|值|
>|:-|:------|
>|CLASSPATH|.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar|
>|JAVA_HOME|D:\idesignApplication\jdk\jdk1.7|
>|Path|;%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin|  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;最后我们打开cmd命令行，校验一下配置是否正确，命令行输入“java -version”，终端输出如下，说明配置无误。  
![](https://i.imgur.com/Pm5Es1k.png)  
### 3、Android studio下载安装  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;打开上面给出的android studio下载地址，这里我们在安卓中文社区下载的，更新没有google官方快，但是省去翻墙，也不会晚太多，可以在国内下载使用。  
![](https://i.imgur.com/a7omQ3R.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;选择对应的平台版本下载下来，双击安装，一路点击“Next”可以安装完成。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这里要注意，在第一次打开的时候可能会报一个错误“Unable to access Android SDK”，如下图。
![](https://i.imgur.com/b1eT8HX.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这是因为加载不到SDK的原因，这里我们直接点“Cancel”，继续后面的步骤，进去以后再加载SDK就可以了。  
### 4、加载SDK
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;安装完成进入android studio之后，在工具栏找到SDK Manager，点击进去，选择加载SDK。
![](https://i.imgur.com/ngF0TcZ.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;进入SDK Manager之后，界面如下：
![](https://i.imgur.com/1K1TonA.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在SDK Platforms标签下，可以看到各个版本的SDK库，选中右下角的“show Package Details”，可以看到更详细的分类，这里勾选需要的版本，点击右下角“Apply”按钮下载。下载完成之后，点击切换到SDK Tools的标签下面，找到“Android SDK Build-Tools”，选在对应的版本下载下来。  
![](https://i.imgur.com/itkiqFM.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;到此我们就完成了Android开发工具以及环境的最基本的配置。