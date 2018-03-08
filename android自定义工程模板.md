---
title: Android Studio模板
date: 2018-02-28 11:58:41
tags: [基础知识,开发环境和配置]
categories: android
---
<img src="https://i.imgur.com/kpfqJDI.jpg" width="100%"/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;“Stop Trying to Reinvent the Wheel”,不要重复造轮子，每个程序员入行就会被告知这条准则。技术更新非常快，我们需要不停地学习，不要把时间浪费在重复劳动上面。虽说未必能达到造轮子的水准，但是制作一些模板，尽可能地避免重复工作还是非常必要的。
<!--more-->
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;日常工作中，使用模板，将会使我们的工作事半功倍，极大地提高工作效率。Google为了方便开发者，在Android Studio内置了三种模板，我们来了解下。  

|模板|作用范围|配置路径|  
|:-:|:-:|:-:|  
|Live templates|代码块|Settings->Editor->Live Templates|  
|File templates|单文件创建|Settings->Editor->File and Code Templates|  
|Plugins templates|多文件创建|AS安装目录\plugins\android\lib\templates\activities|
### Live templates  
![](https://i.imgur.com/KRLnQCD.png)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;首先我们进入Android Studio中Live Templates对应的设置页。这里有Google为了方便开发者默认设置好的很多的Template Group，每个Group里面有很多的Tamplate，这里以Android这个Group为例。
![](https://i.imgur.com/xwOm1MF.png)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;我们可以看到名为Android的Template Group下面有很多的Live Template。鼠标选中第一个，看到界面如下：
![](https://i.imgur.com/pwRDlMq.png)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;可以在“Abbreviation”输入框处为Template指定名字，在“Template text”输入需要简化的语句或者代码块，并且点击底部的“Applicate in ..”指定适用的文件类型和语句块。在语句中使用“$...$”表示待输入的变量，每次输入的时候，相同的变量会一起改变，比如语句中有两个变量“$count$”，则给前一个变量赋值的时候，后面一个变量的值也会随之改变。
![](https://i.imgur.com/7qTrxkt.png)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;可以使用“Edit variables”对创建的Live Template进行一些特殊修改。
![](https://i.imgur.com/vvg5GVW.png)

|Name|Expression|Default value|Skip if defined|  
|:-:|:-:|:-:|:-:|  
|定义在$..$中的变量名|赋予变量特殊值|默认值|使用时是否跳过编辑|  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Expression里面有很多函数，例如className()、date()、methodName()等等。“Skip if defined”不勾选，光标就停在变量处；如果勾选了，光标就会移动到生成的语句或者代码块末尾。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;配置好Live template，在代码中输入对应的key就会得到相应的提示，敲下Enter或者Tab就可以输出对应的语句或者代码块。
![](https://i.imgur.com/kU7nftl.gif)  
>设置位置：Settings->Editor->Live Templates  
>作用：简化一些常用的语句、常用的代码块

### File templates
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在创建文件的时候，Android Studio提供了一些模板，如java、Singleton等，在创建后就自动生成模板的代码，一般用于单文件级别的代码模板。注释可以引用header来修改，也可以整个模板写进去。  
![](https://i.imgur.com/QlUDMEa.png)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;进入到Android Studio的File templates设置页，这里的“Files”标签页对应的是文件模板，“Includes”标签页是定义的一些header之类的引用模板，“Code”和“Other”标签下面的代码模板是不可以新建和删除的，只能对默认生成的文件进行修改。
#### 用法
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在android项目中大家最常用的是列表，这里以RecyclerView适配器代码为例创建一个模板。首先点击“+”新建一个名叫“RecyclerViewAdapter”的File。
![](https://i.imgur.com/nviuJGb.png)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;添加模板代码

<pre>#if (${PACKAGE_NAME} != "")package ${PACKAGE_NAME};#end

import android.content.Context;
import android.support.v7.widget.RecyclerView;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;

#parse("File Header.java")
public class ${FILE_NAME} extends RecyclerView.Adapter<${FILE_NAME}.${VIEW_HOLDER_NAME}> #if (${INTERFACES} != "")implements ${INTERFACES} #end {

    private Context mContext;
    private LayoutInflater mLayoutInflater = null;

    public ${FILE_NAME}(Context context) {
        mContext = context;
        mLayoutInflater = LayoutInflater.from(mContext);
    }

    @Override
    public ${VIEW_HOLDER_NAME} onCreateViewHolder(ViewGroup parent, int viewType) {
        return null;
    }

    @Override
    public void onBindViewHolder(${VIEW_HOLDER_NAME} holder, int position) {

    }

    @Override
    public int getItemCount() {
        return 0;
    }
    
    static class ${VIEW_HOLDER_NAME} extends RecyclerView.ViewHolder{
        public ${VIEW_HOLDER_NAME}(View itemView) {
            super(itemView);
        }
    }
}  </pre>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;保存好模板后，我们在New下面就可以找到对应的模板，输入对应变量之后就可以直接生成我们所需要的文件。
![](https://i.imgur.com/8l8PqDp.gif)
>设置位置：Settings->Editor->File and Code Templates  
>作用：使用单文件创建，只能处理当前文件

### Plugins templates
