# 部署到一个设备

当你的应用程序正在开发中，使用ionic serve或者模拟器在浏览器上测试你的应用程序是迅速、简单和方便的，但是最终你必须在一台设备上测试它。不仅仅是因为这是精确检测你的应用程序会怎样行为和表现，而且很多[Ionic 原生](http://ionicframework.com/docs//native/)插件只有当他们运行在特定的硬件上时才会工作。



## 安卓设备

部署项目到一个安卓设备是相当直接的过程。如果你有一个正在工作的安卓开发环境，你就可以准备开始了。

### 要求

+ [Android Studio](https://developer.android.com/studio/index.html)
+ 更新安卓SDK工具，平台以及依赖组件。可以通过Android Studio的SDK管理器获得。

### 运行你的应用程序

为了运行你的应用程序，所有你需要做的就是在你的安卓设备上启用USB调试和开发

者模式，然后在你的命令行运行ionic run android --device。

这会生成你的应用程序的一个调试版本，和你的安卓和Ionic的代码都相关。

启用USB调试和开发者模式可能会在设备间变化，但是使用谷歌搜索查找是简单的。

你也可以在安卓文档上查看设备开发人员选项。

### 产品构建

运行或构建你的应用程序产品，运行

```
ionic run android --prod --release
# or
ionic build android --prod --release
```

这会作为Ionic的代码源减少程序的代码并且删除任何APK的调试功能。当部署一个一个应用程序到谷歌应用商店时这种方式是普遍使用的。



## iOS设备

不像安卓，iOS开发者需要生成一个配置文件代码签署它们的应用程序进行测试。好消息是，作为iOS9，没有付费的苹果开发者账号，你也可以在你的iOS设备上开发和测试。对于想象尝试移动开发的开发者来说，这是特别棒的。

因为这样可以节省费用但是仍然提供了很多一个完整的苹果开发者账户才有的功能。对于全面的细分功能，请查看[苹果的文档](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html#//apple_ref/doc/uid/TP40012582-CH38-SW1)

### 要求

+ Xcode7或者更高
+ iOS9
+ 一个免费苹果ID或者付费苹果开发者账号

### 创建配置文件

为了开始，你需要生成一个配置文件来代码签署你的应用程序

### 使用你的苹果ID

1.打开Xcode的preferences(Xcode>preferences)

2.点击'账号'标签

3.使用你的Apple ID登录(+>Add Apple ID...)

一旦你已经成功登录，一个新的免费‘个人组’会出现在你的苹果ID下方

![profiles](/home/decade/图片/profiles.jpg)

### 使用苹果开发者账号

使用付费苹果开发者账号创建配置文件会包含多一些内容。至于全部的功能，请查看苹果开发者文档中的[在设备上启动应用程序](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/LaunchingYourApponDevices/LaunchingYourApponDevices.html)



### 运行你的应用程序

1.运行你的应用程序构建的产品，使用ionic buld iOS --prod命令

2.打开在Xcode里面platforms/ios/中的.xcodeproj文件

3.通过USB连接你的手机并且选择将它作为运行目标

4.点击Xcode上的播放按钮来尝试运行你的应用程序。



### 编码应用程序签署

接下来，你需要编码签署你的应用程序，怎样去做取决于你运行的是Xcode8还是更早的版本



### Xcode7和更早版本

如果你运行Xcode7或者更早版本，当你尝试运行应用程序，你会得到一个像下图的编码签署错误：

![sign-fail-1](/home/decade/图片/sign-fail-1.jpg)

点击'Fix issue'按钮，然后选择你的‘个人组’文件

![team-menu-1](/home/decade/图片/team-menu-1.jpg)

### Xcode8

如果你正在运行Xcode8，编码签署错误会出现作为一个建造时间错误，而不是作为弹出错误：![code-sign-err-xcode8](/home/decade/图片/code-sign-err-xcode8.png)

要选择证书，以签署你的应用程序，做以下内容：

1.单机“Project Navigator”中的名称或项目转到“Project Editor”。

2.选择“General”部分。

3.在‘Singing’部分下拉菜单的‘Team’中选择与你的签署证书有关的团队伙伴。

![code-sign-xcode8](/home/decade/图片/code-sign-xcode8.png)

### 信任证书

一旦你编码签署了你的应用程序，你应该会得到一个像这样的启动错误。你会自动看到这个错误在Xcode7或者以下版本上。在Xcode上它会出现在你下一次尝试运行应用程序时：

![launch-fail-1](/home/decade/图片/launch-fail-1.jpg)

为了通过，我们必须告诉iOS设备新人我们编码签署的证书：

1.打开在你iOS设备上的"Setting"应用程序。

2.转到‘General>Device Management’。你会看到和你Apple ID联系的邮箱账号或者你用来签署你应用程序的苹果开发者账号。

3.点击邮箱地址

4.点击‘Trust <your_email>’：

![verify](/home/decade/图片/verify.jpg)

现在，返回Xcode并且点击播放按钮或者在命令行运行ionic run ios -- device 来在iOS设备安装和启动你的应用程序。