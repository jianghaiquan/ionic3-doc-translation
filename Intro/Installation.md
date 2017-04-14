# 安装 Ionic

Ionic2应用程序主要是通过Ionic命令行工具(CLI)来被创建和开发的，它使用Cordova(驱动PhoneGap的核心引擎)来建立和部署为一个本地应用程序。这意味着我们需要安装一些工具来进行开发。

## Ionic和Cordova

为了创建Ionic2项目，你需要安装最新版本的CLI和Cordova。在你做这些之前，你需要安装最近版本的Node.js。为了本地应用程序的开发，[下载和安装](https://nodejs.org/)Node.js6或者更高版本然后继续安装Ionic CLI和Cordova。

```
$ npm install -g ionic cordova
```

>你可能需要添加"sudo"在这些命令前面去全局安装这个工具

一旦完成，创建你的第一个Ionic应用程序：

```
$ ionic start cutePuppyPics --v2
```

如果你想用Ionic1就省略--v2。使用cd进入创建的文件夹然后运行inonic server命令在浏览器测试你的应用程序！

```
$ cd cutePuppyPics
$ ionic serve
```

## Platform Guide

对于那些构建本地应用程序的iOS和Android(大多数人！)，在你能够进行最大程度的Ionic和Cordova开发之前，每个平台都有具体的特征和安装要求。

对于iOS开发者，看一看[Cordova iOS Platform Guide](https://cordova.apache.org/docs/en/latest/guide/platforms/ios/)，根据介绍安装或者升级Xcode,并且可以注册一个开发者账户来开始构建iOS应用程序。

对于安卓开发者，看一看Cordova Andorid Platform Guide，根据介绍安装SDK和Android Studio来开始构建安卓应用程序。