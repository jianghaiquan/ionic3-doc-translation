# 动作表单 Cordova / PhoneGap Plugin
by [Eddy Verbruggen](http://twitter.com/eddyverbruggen)

## 0. Index

1. [描述  ](#1-description)
2. [截图](#2-screenshots)
3. [安装](#3-installation)
4. [用法](#4-usage)
5. [开发者](#5-credits)
6. [许可声明](#6-license)

## 1. Description

展现一个用户可以选择的多选项的表单

* 兼容 [Cordova Plugman](https://github.com/apache/cordova-plugman)
* iOS 原生使用 `UIActionSheet`
* Android 原生使用 `AlertDialog`
* WP8 原生使用 `Popup`

## 2. Screenshots

iOS

<img src="https://raw.githubusercontent.com/EddyVerbruggen/cordova-plugin-actionsheet/master/screenshots/ios/ios-share.png" width="235"/>&nbsp;
<img src="https://raw.githubusercontent.com/EddyVerbruggen/cordova-plugin-actionsheet/master/screenshots/ios/ios-delete.png" width="235"/>&nbsp;
<img src="https://raw.githubusercontent.com/EddyVerbruggen/cordova-plugin-actionsheet/master/screenshots/ios/ios-logout.png" width="235"/>


Android

<img src="https://raw.githubusercontent.com/EddyVerbruggen/cordova-plugin-actionsheet/master/screenshots/android/android-share.png" width="235"/>&nbsp;
<img src="https://raw.githubusercontent.com/EddyVerbruggen/cordova-plugin-actionsheet/master/screenshots/android/android-delete.png" width="235"/>&nbsp;
<img src="https://raw.githubusercontent.com/EddyVerbruggen/cordova-plugin-actionsheet/master/screenshots/android/android-logout.png" width="235"/>

Windows Phone 8

<img src="https://raw.githubusercontent.com/EddyVerbruggen/cordova-plugin-actionsheet/master/screenshots/wp8/wp8-share.jpg" width="235"/>&nbsp;
<img src="https://raw.githubusercontent.com/EddyVerbruggen/cordova-plugin-actionsheet/master/screenshots/wp8/wp8-delete.jpg" width="235"/>&nbsp;
<img src="https://raw.githubusercontent.com/EddyVerbruggen/cordova-plugin-actionsheet/master/screenshots/wp8/wp8-logout.jpg" width="235"/>

## 3. Installation

### 自动安装 (CLI / Plugman)
```
$ cordova plugin add cordova-plugin-actionsheet
$ cordova prepare
```

ActionSheet.js is brought in automatically. There is no need to change or add anything in your html.

ActionSheet.js会被自动引用。在你的html不需要修改和添加任何东西。

### PhoneGap Build
ActionSheet  works with PhoneGap build too! Just add the following xml to your `config.xml` to always use the latest version of this plugin:

ActionSheet同样可以在PhoneGap项目中使用，你只需要把下面的代码加入到你的`config.xml`就可以使用这个插件的最新版本。

```xml
<plugin name="cordova-plugin-actionsheet" />
```

ActionSheet.js is brought in automatically. Make sure though you include a reference to cordova.js in your index.html's head:

ActionSheet.js会被自动个引用。确保在你的index.html的头部引用了如下的代码
```html
<script type="text/javascript" src="cordova.js"></script>
```

## 4. Usage

### 展示

这个demo能让你快速构建一个例子 [demo code](demo) 

or copy-paste some of the code below to replicate the ActionSheets of the screenshots above.

或者复制粘贴下面的一些代码来重现上述的截图

Also, wait for `deviceready` to fire before using plugins in general!

当然，等待`deviceready`之后才能正常的使用这个插件

```js
  var callback = function(buttonIndex) {
    setTimeout(function() {
      // like other Cordova plugins (prompt, confirm) the buttonIndex is 1-based (first button is index 1)
      alert('button index clicked: ' + buttonIndex);
    });
  };

  function testShareSheet() {
    var options = {
        androidTheme: window.plugins.actionsheet.ANDROID_THEMES.THEME_DEVICE_DEFAULT_LIGHT, // default is THEME_TRADITIONAL
        title: 'What do you want with this image?',
        subtitle: 'Choose wisely, my friend', // supported on iOS only
        buttonLabels: ['Share via Facebook', 'Share via Twitter'],
        androidEnableCancelButton : true, // default false
        winphoneEnableCancelButton : true, // default false
        addCancelButtonWithLabel: 'Cancel',
        addDestructiveButtonWithLabel : 'Delete it',
        position: [20, 40], // for iPad pass in the [x, y] position of the popover
        destructiveButtonLast: true // you can choose where the destructive button is shown
    };
    // Depending on the buttonIndex, you can now call shareViaFacebook or shareViaTwitter
    // of the SocialSharing plugin (https://github.com/EddyVerbruggen/SocialSharing-PhoneGap-Plugin)
    window.plugins.actionsheet.show(options, callback);
  };

  function testDeleteSheet() {
    var options = {
        'addCancelButtonWithLabel': 'Cancel',
        'addDestructiveButtonWithLabel' : 'Delete note'
    };
    window.plugins.actionsheet.show(options, callback);
  };

  function testLogoutSheet() {
    var options = {
        'buttonLabels': ['Log out'],
        'androidEnableCancelButton' : true, // default false
        'winphoneEnableCancelButton' : true, // default false
        'addCancelButtonWithLabel': 'Cancel'
    };
    window.plugins.actionsheet.show(options, callback);
  };
```

On iOS, you can also position the actionSheet origin by adding `position: [100, 200]`

在ios下，你可以添加`position: [100, 200]`字段来自定义actionSheet的初始位置
### 隐藏

If for some reason you want to hide the actionsheet programmatically, do this:

出于某种原因你想要使用代码来隐藏这个actionsheet，使用下面的方法
```js
  // options and callbacks are optional, so either approach will work:
  window.plugins.actionsheet.hide();
  window.plugins.actionsheet.hide({}, onSuccess, onError);
```

## 5. Credits
iOS 和 WP8 代码: [Eddy Verbruggen](https://github.com/EddyVerbruggen)

Android 代码: 大部分出自于 [Brill Papping](https://github.com/bpappin)


## 6. Change history
* 2.3.3 Default iPad popup is now in the center (was in the top left corner)
* 2.3.1 Added `subtitle` (iOS) and `destructiveButtonLast` preferences. Also, iOS now uses the newer `UIAlertController` instead of `UIActionSheet`.
* 2.2.2 OK, 2.2.1 has issues with Russian and the like, so reverted. Just add `<meta charset="utf-8" />` to your html file.
* 2.2.1 Encoding of diacritical characters fixed on iOS, so you can now use `Español` as a title or button label.
* 1.1.6 You can now set the iOS actionSheet origin position (uses the iOS `actionSheet.showFromRect` method)
* 1.1.2 You can now select a theme for your Android popup, see the first example above

## 7. License

[The MIT License (MIT)](http://www.opensource.org/licenses/mit-license.html)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

对于任何想拷贝这个插件，或者想要相关文档的人，（作者）完全免费的开放使用这个插件的使用权限，
你可以毫无约束的使用它，包括但不限于权限、复制、修改、合并、发布、分发、再许可，和/或出售此软件的副本，
但是如果你有这些想法，请你遵循下列条件规则：

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

上述的版权说明和许可说明应该保存在所有的软件副本的正文当中。

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

这个软件照这种方式提供，分享就可以了，不需要其他任何或明或暗的种类的担保，包括但不限于销售性的行为，
对于想要达成某些特定的目的或者一些侵权性行为，在任何情况下，无论是商业，侵权或者其他方面，作者或版权人都要为其行为负责。

