# Ionic2 辅助

现在你有了[Ionic和它的依赖安装](http://ionicframework.com/docs/intro/installation)，你可以构建你的第一个应用程序!这一节会通过开始一个新应用的过程来引导你开始一个新应用，添加页面，在这些页面之间导航并且还有更多。让我开始吧！

> Ionic使用TypeScript来编码，如果你不熟悉TypeScript,看看[这个页面](http://ionicframework.com/docs//resources/what-is/#typescript)。

## 开始一个新的Ionic2应用程序

开始一个新的应用程序很简单！从你的[命令行](http://ionicframework.com/docs//resources/what-is/#cli),运行命令：

```
$ ionic start MyIonic2Project tutorial --v2
```

+ start会告诉CLI创建一个新的应用程序。
+ MyIonic2Project是文件名和你工程中的应用程序名。
+ tutorial是你工程中的启动器模板
+ --v2告诉CLI你想要一个2.0工程

随着项目的创建，这也将为应用安装[npm模块](http://ionicframework.com/docs/resources/what-is/#npm),并且设置好[Gordova](http://ionicframework.com/docs/resources/what-is/#cordova)准备运行。

如果辅助模板不是你想用的，Ionic有一些可用的模板：

+ tabs:一个简单的3标签布局
+ sidemenu：一个有侧边swipable菜单的布局
+ blank：一个单页的空白启动器
+ tutorial:一个被引导的启动项目

如果你不通过运行ionic start MyIonic2Project --v2来制定一个模板，tabs模板会被使用。



## View the app in a browser

现在，你可以用cd进入你创建的文件夹，使用serve命令，来在浏览器对你的应用程序来一个快速预览。

```
$ cd MyIonic2Project/
$ ionic serve
```

![tutorial-screen](/home/decade/图片/tutorial-screen.png)

如果一切都安装成功，你应该可以看到上面的欢迎信息。

在下一节，让我们检查通过ionic start命令创建的项目结构。