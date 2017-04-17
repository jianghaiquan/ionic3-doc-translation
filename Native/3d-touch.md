# 3D触摸 Cordova plugin （只支持ios）
作者 [Eddy Verbruggen](http://twitter.com/eddyverbruggen)
git地址 [git](https://github.com/EddyVerbruggen/cordova-plugin-3dtouch)
## 0. Index

1. [描述](#1-描述)
2. [截图](#2-截图)
3. [安装](#3-安装)
4. [用法](#4-用法)
5. [静态桌面图标动作](#5-静态主页图标事件)
6. [更新日志](#6-更新日志)

## 1. 描述

添加此功能到你的cordova app之后可以实现如下功能:
* 静态或者动态的桌面图标的快捷动作.
* 启用外部链接的链接预览.

## 2. 截图

<img src="https://raw.githubusercontent.com/EddyVerbruggen/cordova-plugin-3dtouch/master/screenshots/icon-actions-2.PNG" width="235"/>&nbsp;
<img src="https://raw.githubusercontent.com/EddyVerbruggen/cordova-plugin-3dtouch/master/screenshots/icon-actions-4.PNG" width="235"/>&nbsp;
<img src="https://raw.githubusercontent.com/EddyVerbruggen/cordova-plugin-3dtouch/master/screenshots/link-preview.PNG" width="235"/>&nbsp;

## 3. 安装

用npm安装最新的版本
```
$ cordova plugin add cordova-plugin-3dtouch
```

从github安装:
```
$ cordova plugin add https://github.com/EddyVerbruggen/cordova-plugin-3dtouch
```

`ThreeDeeTouch.js` 会被自动引用.
它添加了一个全局ThreeDeeTouch对象来让你和这个插件互动
## 4. 用法

可以先看个例子[demo code](https://github.com/EddyVerbruggen/cordova-plugin-3dtouch/blob/master/demo/index.html) 这里介绍了很多用法，安装插件后复制粘贴之后就能运行了.

请确保deviceready完成后再来调用这些function

注意，所有这些function都有可自定义的callback,但是绝大部分没什么卵用，除了这里的第一个函数：

### 是否支持此功能
你需要一台肾6S或者其他更高端的更高级的设备来使用这个特性，
所以说你可以试试是否支持这个插件。

```js
  ThreeDeeTouch.isAvailable(function (avail) {
    // 'avail' is a boolean
    alert("avail? " + avail)
  });
```

### 监听有效的触发事件

You can get a notification when the user force touches the webview.

当用户有效触发时，会得到一条通知，

The plugin defines a Force Touch when at least 75% of the maximum force is applied to the screen.

插件定义有效触发的触发条件为：至少有75%屏幕的距离被触摸

Your app will receive the x and y coordinates, so you have to figure out which UI element was touched.

你的app将会接收到X,Y的坐标，所以你要用接收到的这些坐标来处理被touch 到的ui元素

Useful for context menu's, zooming in on images, whatnot.

比如上下文菜单，放大图像，等等

```js
  ThreeDeeTouch.watchForceTouches(function(result) {
    console.log("force touch % " + result.force); // 84
    console.log("force touch timestamp " + result.timestamp); // 1449908744.706419
    console.log("force touch x coordinate " + result.x); // 213
    console.log("force touch y coordinate " + result.y); // 41
  });
```

You can also track in JS which was the last element that received an `ontouchstart` event,

你也可以在js里进行跟踪监听来获取最新触发 `ontouchstart` event的元素

remember the timestamp when that happened and correlate that to the timestamp of the force touch.

记录下事件发生的时间戳，然后将这个时间戳与推动触摸的时间戳关联起来

If those are very close to each other you can safely assume the force touch was on that element.

如果两个时间点很接近你就可以几乎断定此次事件触发在那个元素上

### 配置快捷操作

When your app starts you can add those fancy Quick Actions to the Home Screen icon.

当你APP启动时你可以在主屏幕icon上添加这些快捷操作

You can configure up to four icons and they are 'cached' until you pass in a new set of icons.

您可以配置多达四个图标，他们会一直'缓存'直到你通过一组新的图标来代替他们

So you don't need to do this every time your app loads, but it can't really hurt.

所以你不需要每次启动APP都这样做,但是如果每次启动APP都这样做的话也无伤大雅

There are two types of icons supported currently `iconType` and `iconTemplate`.

目前支持2种icon 分别是`iconType` and `iconTemplate`.

##### iconType
A value from a (case insensitive) fixed list of icons which have been provided by Apple and look great:

APPLE自带的从一个固定图标列表里的取得一个value值（不区别大小写），看上去不错，value值如下所示：

* iOS 9.0: Compose, Play, Pause, Add, Location, Search, Share
* iOS 9.1 added these: Prohibit, Contact, Home, MarkLocation, Favorite, Love, Cloud, Invitation, Confirmation, Mail, Message, Date, Time, CapturePhoto, CaptureVideo, Task, TaskCompleted, Alarm, Bookmark, Shuffle, Audio, Update

APPLE的icon库 [here](https://developer.apple.com/ios/human-interface-guidelines/graphics/system-icons/#quick-action-icons)

##### iconTemplate
Can be used to provide your own icon. It must be a valid name of an icon template in your Assets catalog.

你可以自定义你自己的icon，它必须是您的项目目录中的图标模板的有效名称。

The `type` param is the most convenient way to relate the icon to the event you'll receiver when
the icon was used to launch your app. So make sure it's unique amongst your icons.

当这个图标用来启动你的应用程序的时候，接受'type' 参数是你能接受到的能将图标与事件关联起来的最便捷的方法。所以确保它是独一无二的图标。

```js
  ThreeDeeTouch.configureQuickActions([
    {
      type: 'checkin', // optional, but can be used in the onHomeIconPressed callback
      title: 'Check in', // mandatory
      subtitle: 'Quickly check in', // optional
      iconType: 'Compose' // optional
    },
    {
      type: 'share',
      title: 'Share',
      subtitle: 'Share like you care',
      iconType: 'Share'
    },
    {
      type: 'search',
      title: 'Search',
      iconType: 'Search'
    },
    {
      title: 'Show favorites',
      iconTemplate: 'HeartTemplate' // from Assets catalog
    }
  ]);
```

### 首页图标按压事件
When a home icon is pressed, your app launches and this JS callback is invoked. I found it worked
reliable when you use it like this (you should recognize the `type` params used previously):

当首页图标被按压时，你的APP启动，然后这个js callback 被调用,我发现当你这样使用它时，他运行的非常好（你应该事先识别使用的type参数）

```js
  document.addEventListener('deviceready', function () {
    ThreeDeeTouch.onHomeIconPressed = function (payload) {
      console.log("Icon pressed. Type: " + payload.type + ". Title: " + payload.title + ".");
      if (payload.type == 'checkin') {
        document.location = 'checkin.html';
      } else if (payload.type == 'share') {
        document.location = 'share.html';
      } else {
        // hook up any other icons you may have and do something awesome (e.g. launch the Camera UI, then share the image to Twitter)
        console.log(JSON.stringify(payload));
      }
    }
  }, false);
```

### 启用链接预览
UIWebView and WKWebView (the webviews powering Cordova apps) don't allow the fancy new link preview feature
of iOS9. If you have a 3D Touch enabled device though, you sometimes are allowed to force press a link and a
preview pops up (see the screenshot above). If you want to enable this feature, do:

对于ios9来说，UIWebView和wkwebview(cordova app的驱动)不允许新链接预览功能。如果你有一个具有3D触摸功能的设备，有时你被允许点击一个链接和一个
预览弹出（见上面的截图）。如果要启用此功能：

```js
  ThreeDeeTouch.enableLinkPreview();
```

### 禁用链接预览
To disable the link preview feature again, do:

想要禁用链接预览，使用下面这个方法。

```js
  ThreeDeeTouch.disableLinkPreview();
```

## 5. 静态主页图标事件

The `configureQuickActions` function above can add dynamic icon actions to your app,
but what if you want to have actions immediately after installation from the AppStore, before opening your app?

上述的`configureQuickActions` function可以给你的app添加动态的图标事件

That's where static icons come in, which need to be configured in your app's `.plist` file. Let's say you want these actions:

所以有动态的，肯定就有静态啦 ，这里就要去修改你app的`.plist`文件，假设你想要这些事件

<img src="screenshots/icon-action-2-static.jpg" width="360" height="223"/>

把这个加到你的 `.plist`里:

```xml
	<key>UIApplicationShortcutItems</key>
	<array>
		<dict>
			<key>UIApplicationShortcutItemIconFile</key>
			<string>Eye</string>
			<key>UIApplicationShortcutItemTitle</key>
			<string>Eye from plist</string>
			<key>UIApplicationShortcutItemSubtitle</key>
			<string>Awesome subtitle</string>
			<key>UIApplicationShortcutItemType</key>
			<string>eyefromplist</string>
		</dict>
		<dict>
			<key>UIApplicationShortcutItemIconType</key>
			<string>UIApplicationShortcutIconTypeCompose</string>
			<key>UIApplicationShortcutItemTitle</key>
			<string>Compose</string>
			<key>UIApplicationShortcutItemType</key>
			<string>compose</string>
		</dict>
	</array>
```

#### UIApplicationShortcutItemIconFile（设置标签的Icon文件）

The second action uses the built-in `UIApplicationShortcutIconTypeCompose` icon
(which is the same as the `Compose` icon you'd get when using the `configureQuickActions`),

第二个事件是使用内置的`UIApplicationShortcutIconTypeCompose` 图标
和当你使用`configureQuickActions`时与`Compose` 图标相同

but the first one uses a custom icon: `Eye`. This expects an `Eye.png` file in your app's bundle.

但是第一种使用了一个自定义图标`Eye`.这东西在你的APP里捆绑了一个`Eye.png`文件

According to Apple's docs this needs to be a single color square 35x35 icon, but that will look pixelated
on retina devices, so go ahead and use a 70x70 or 105x105 icon if you please.

根据苹果的文档，这需要一个单一颜色的35*35的方形塔图标，但是那样在呈现时就会看到不少像素点，所以使用70X70或者105的图来更好的呈现效果。

In Xcode just drag the icon to the `Resources` folder. If you're using [Telerik Platform](https://platform.telerik.com)
you can add it to the `App_Resources/iOS` folder. That's where the `.plist` is stored as well.

在xcode上只要把图标拖动到`Resources`文件夹.如果你使用了 [Telerik 平台](https://platform.telerik.com)
你可以把它放到`App_Resources/iOS`文件夹，这里就是.plist文件存储的地方，这种方法也无妨

#### UIApplicationShortcutItemTitle / UIApplicationShortcutItemSubtitle（设置标签的title）

You can guess what those do by looking at the screenshot, right?

你可以通过看截图猜出那些是做什么的，对吧？

Note that you can localize these by opening Xcode, and adding a `InfoPlist.strings` file to the `Resources` folder.
Then mark it as Localizable in the Utilities window and add translations for the appropriate languages. [Details here.](https://kb.applingua.com/2011/10/how-to-localize-app-names/)

你可以通过xcode来改变它,在`Resources` 文件夹里加入`InfoPlist.strings`文件，然后在工具窗口将其标记为可定义的，再用你觉得合适的语言去解释它[更多细节](https://kb.applingua.com/2011/10/how-to-localize-app-names/)

If you're using Telerik Platform you can manually upload this plugin and tweak the plugin's contents.
See the commented section in `plugin.xml` about static icon localization.

如果你在使用telerik平台你可以手动上传这个插件或者调整插件的内容

#### UIApplicationShortcutItemType（设置标签的类型）
This is the same as the `type` param of `configureQuickActions`, so it's what you'll receive in your

`onHomeIconPressed` as `payload.type`. Just do something cool with that info.
这个和 `configureQuickActions` 里的`type`参数一样，所以你可以在`onHomeIconPressed`事件中`payload.type`用收到它。嗯 ，用它好好做你想做的事吧。

## 6. 更新日志
* 1.3.6 Get back the subtitle when a home icon was pressed, thanks [#27](https://github.com/EddyVerbruggen/cordova-plugin-3dtouch/issues/27)!
* 1.3.5 Home icons are now WKWebView compatible. Previously your app would crash. See [#12](https://github.com/EddyVerbruggen/cordova-plugin-3dtouch/issues/12).
* 1.3.4 Increased the wait time for `onHomeIconPressed` from 5 to 15 secs. See [#4](https://github.com/EddyVerbruggen/cordova-plugin-3dtouch/issues/4).
* 1.3.3 Compatibility of 'home icon cold-starts' with [Meteor](https://www.meteor.com), see [#4](https://github.com/EddyVerbruggen/cordova-plugin-3dtouch/issues/4).
* 1.3.2 Compatibility with Cordova-iOS 4.
* 1.3.1 Added `timestamp` to the response of `watchForceTouches`.
* 1.3.0 You can now receive notifications when the user applies a 'Force Touch' on the webview.
* 1.2.2 Documentation on how to localize the title and subtitle of your static icons.
* 1.2.1 Documentation on how to add static icons to your app.
* 1.2.0 iOS 9.1 added a lot of new iconTypes to choose from. Thanks [#2](https://github.com/EddyVerbruggen/cordova-plugin-3dtouch/issues/2)!
* 1.1.0 Found a solid way to deal with timing when to call into `onHomeIconPressed`. Should always work now, even on coldstart.
* 1.0.1 Increased the timeouts a bit, so there is a better chance `onHomeIconPressed` gets called on coldstart. Thanks [#1](https://github.com/EddyVerbruggen/cordova-plugin-3dtouch/issues/1).
* 1.0.0 Initial release (untagged)
