---
title: android项目结构
date: 2018-02-27 14:44:12
tags: [基础知识,开发环境和配置]
categories: android
---
<img src="https://i.imgur.com/dtFmRqb.jpg" width="100%"/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;本文主要介绍Android studio工具里android工程的目录结构，各包、文档的作用，以及对比和Eclipse下android的工程目录结构的不同之处。
<!--more-->
## 不同IDE下android工程结构的对比
### 1、Eclipse下目录结构
![](https://i.imgur.com/l0VhnxL.png)  
 **src**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这里存放的是java代码。  
 **gen**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这里存放R.java文件，该文件自动标识了资源的索引。  
 **Android 4.4W**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4.4W是android平台版本，对应于API 20，该文件里面包含了android.jar文件，里面关联了Android的API。  
 **Android Private Libraries**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;这里存放的是libs目录下jar包的映射，libs里的jar包引用视为私有引用，也就是第三方的库。添加jar包到libs里面会自动添加引用到Android Private Libraries里面，移除libs目录的jar包，这里的引用也会自动移除。  
 **JRE System Library**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;对应于JDK安装后的jre目录核心类库，表示系统类库文件，这里存放的jar包是java运行依赖的类库。  
 **Android Dependencies**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;该文件包含了工程引用的library。  
 **assets**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;放置原生文件，里面的文件会保留原有格式，文件袋额读取需要通过流。  
 **bin**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;放置工程编译后生成的文件，以及apk安装包。  
 **libs**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;放置引用的第三方库类文件。  
 **res**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;项目的资源文件，里面按文件夹分类存放图片、布局等资源文件，会在R.java文件中自动生成索引。  
 **AndroidManifest.xml**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;android工程的主配置清单文件，配置了应用的基本信息，应用名称、icon、包名、版本、权限、组件、应用程序入口等，应用启动前先访问主配置清单文件。  
 **proguard-project.txt 和 project.properties**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;代码混淆文件。  
### 2、Android Studio下目录结构  
![](https://i.imgur.com/RbEOaYY.png)    
 **.gradle**  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;gradle运行构建时自动生成的文件，不需要更改，也不需要纳入源码管理。  
 **.idea**  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;IDE运行时自动生成的文件，不需要更改，也不需要纳入源码管理。  
 **app**  
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;一个module，每一个module都类似于Eclipse里面的一个Project，module结构和父项目结构类似。  
![](https://i.imgur.com/ke2lT2n.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**build**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;编译时自动输出的文件，不需要更改，也不需要纳入源码管理。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**libs**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;app模块引用的第三方类库文件，需要的第三方jar文件放这里，.so文件也放这里。可以在Project Structure中管理它的依赖关系，也可以在build.gradle中直接修改。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**src**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;module源码所在目录。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**androidTest**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Android Studio生成的测试模块，可删。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**main**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;module源码目录。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**test**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;单元测试模块，可删。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**.gitignore**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;module中git管理源码的配置文件。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**app.iml**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;module中IDE生成的文件。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**build.gradle**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;module自动编译的配置文件。  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**proguard-rules.pro**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;module中代码混淆配置文件。  
 **build**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;编译时自动输出的文件，不需要更改，也不需要纳入源码管理。  
 **gradle**  
![](https://i.imgur.com/nbLeTek.png)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;gradle目录下有个wrapper目录，里面有两个文件，里面是对gradle的配置信息。来看下gradle-wrapper.properties里面的内容：  
```
distributionBase=GRADLE_USER_HOME  
distributionPath=wrapper/dists  
zipStoreBase=GRADLE_USER_HOME  
zipStorePath=wrapper/dists  
distributionUrl=https\://services.gradle.org/distributions/gradle-4.1-all.zip    
```
可以看到里面声明了gradle的目录、下载路径、版本等信息。  
 **.gitignore**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;git对源码管理的配置文件，可以在里面添加你不希望纳入源码管理的文件。  
 **build.gradle**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;项目的编译环境配置文件，gradle最主要的配置文件，这里是对整个project的配置，代码如下：
```
// Top-level build file where you can add configuration options common to all sub-projects/modules.
buildscript {
    
    repositories {
        google()
        jcenter()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.0.1'
        // NOTE: Do not place your application dependencies here; they belong
        // in the individual module build.gradle files
    }
}

allprojects {
    repositories {
        google()
        jcenter()
    }
}

task clean(type: Delete) {
    delete rootProject.buildDir
}
```  

这里声明了仓库源，google()，还有个新的jcenter()，jcenter()可以理解成远程仓库，它兼容了maven中心仓库，性能更优；还声明了gradle的版本。  
 **gradle.properties**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;配置gradle运行环境的文件，配置gradle运行时的模式、运行时JVM虚拟机的大小等。  
 **gradlew 和 gradlew.bat**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;前者是linux下的shell脚本，后者是windows下的批处理命令，它们的作用是根据gradle-wrapper.properties文件中的distributionUrl下载对应版本的gradle。这样可以保证在不同的环境下构建都是用的统一的gradle版本，即使没有安装gradle，也会自动下载对应版本的gradle。  
 **local.properties**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;配置android NDK、SDK的地方，一般不纳入源码管理。  
 **settings.gradle**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;声明当前项目包含哪些module，如果多个module，中间用“,”分开，代码如下：
>include ':app1',':app2'

 **ProjectName.iml**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;编译项目时自动生成的文件，文件名一般为“项目名.iml”，是Android Studio识别项目的配置文件，不纳入源码管理。  

### 3、Android Studio相比Eclipse的优势 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;目前Android Studio已经更新到了3.0.1的版本，相对已经比较稳定了，功能也非常强大。2015年Android Studio1.0发布的时候，google就宣布停止对Eclipse的支持，新的API、插件不会考虑Eclipse的支持，所以想要开发Android的童鞋，Android Studio成了首选的工具，而且Android Studio的功能确实也非常强大，相对于Eclipse更加智能，体现在如下几点：  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1、Android studio由google推出，指定的官方工具，后期google工程师肯定会不断完善完美融合Android；  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2、Eclipse响应慢，内存溢出问题一直让人诟病，Android Studio经过几个版本的迭代，已经非常的稳定流畅，体验非常的棒；  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3、更加智能。代码补全更智能，输入时，Android Studio会自动智能预测输入并给出最优提示；自动保存，无需经常Ctrl+C；智能重构、智能预测报错；  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4、整合了Gradle构建工具。Android Studio的一大亮点就是使用Gradle构建，gradle结合了Ant和Maven的有点，不管是配置、编译、打包都非常的方便；  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5、更强大智能的UI编辑器。Android Studio的UI编辑器非常强大智能，吸收了Eclipse+ADT的优点，还自带多屏布局预览，颜色、图片、string可以在布局和代码中可以实时预览；截图带有设备框，可以随时录制模拟器的视频，非常方便；  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;6、内置终端。不需要再打开CMD命令，来回切换界面了，直接在Terminal终端就可以执行命令；  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;7、更完善的插件系统，支持各种插件，Git、Markdown、Gradle等；  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;8、完美整合版本控制，安装时自带Git、Github、SVN等版本控制系统，可以方便的管理代码；  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;9、可以直接打开文件所在位置。即使文件关闭，重新打开依然可以回退操作。图片可以直接转.9图片，自带.9编辑。在gradle编译时使用aar依赖超级方便；  

