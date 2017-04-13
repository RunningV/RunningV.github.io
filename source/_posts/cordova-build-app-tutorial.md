---
title: cordova打包简单教程--android篇
date: 2017-04-11 08:05:29
tags: cordova npm native
---

最近在开发移动端app,html页面开发完成后如何打包成原生app呢？我就去研究了
下`cordova`打包工具，看起来蛮简单，写个入门教程，针对小白用户。

### 1. 安装cordova，命令行输入：
`npm install -g cordova`
请确保你的网络好，最好能翻墙。（用cnpm等国内代理npm的可能会失败）
安装完毕后命令行输入:
`cordova --help`
显示以下内容
!['cordova安装成功输出'](/images/cordova-tutorials/1.png)
后续操作全部基于上图中的`Examples`命令;

### 2. 创建应用项目,在自己想创建项目的目录打开`CLI`，后续命令全部在CLI中执行
`cordova create myApp org.apache.cordava.myApp myApp`
此命令会在当前目录创建myApp项目，目录结构如下图：
!['cordova安装成功输出'](/images/cordova-tutorials/2.png)
创建成功后CLI输出信息如下
!['cordova安装成功输出'](/images/cordova-tutorials/1.2.png)
`cd myApp`
`cordova telemetry on` //此命令未知何用，根据创建完成提示操作
主要内容在`www`目录下；`platforms`与`plugins`目录都为空，下面我们就来添加平台和插件

### 3. 添加插件
我们在app中会调用一些系统的权限或事件，cordova提供了这些插件，现在就来添加一个相机调用插件
`cordova plugin add cordova-plugin-camera --save`
添加成功CLI输出信息如下图：
!['cordova安装成功输出'](/images/cordova-tutorials/3.png)
可以在plugins目录查看到添加的插件信息
### 4 添加平台
添加平台用于打包成原生app,对于android需要提前安装`java`和`android SDK`,
否则无法打包成`android apk`;
`Java`和`Android SDK`的安装自行搜索，这两个略有难度；现在我们添加android平台
`cordova platform add android --save`
添加成功CLI输出如下：
!['cordova安装成功输出'](/images/cordova-tutorials/4.png)
此时可以在`platforms`目录看到`android`资源信息
`cordova requirement android`
由于我开始没有安装`Android SDK`此处报错没有找到`ANDROID_HOME`
!['cordova安装成功输出'](/images/cordova-tutorials/5.png)
***JDK和android SDK的安装教程大家另行搜索，此处安装完成后可能还会遇到其他问题
，希望大家耐心网上搜索答案***
我在电脑安装JDK和SDK成功了，但是输入`cordova requirement android`还是显示以下错误
!['cordova安装成功输出'](/images/cordova-tutorials/5.1.png)
花了半天时间卡在这个地方。我就尝试下一步打包apk

### 5 打包成android apk
我的最终目的是打包成apk安装到手机看效果，所以就没有说去安装android模拟器去调试，
CLI输入以下命令：
```cordova build android --verbose```
如果第一次打包需要下载gradle等其他文件，此处如果没有梯子，90%会一直卡在下载中。
打包完成输出如下：
!['cordova安装成功输出'](/images/cordova-tutorials/6.png)
我打包尝试了5次，最后终于成功可以看到这里花了40多分钟，所以此处成功与否全靠网速和梯子速度。
最后可以去`*\myApp\platforms\android\build\outputs\apk`目录找到打包完成
的`android-debug.apk`安装到手机显示，编辑项目中`www`目录下的文件就是我们前端要开发的内容

### 6 总结
因为本人也是第一次接触Cordova打包工具，此教程只是简单的探索cordova打包过程，
此工具使用其实很简单就是那些命令；但是如果没有梯子不建议尝试。
后续我会继续尝试打包到*IOS*平台，欢迎关注！