# ionic 主题 #

----------

### 一、介绍 ###
我们可以建立一个很容易自定义和修改样式的 app，并且能适应你的品牌。但是仍然要跟着
每个平台的标准。在 app 商店中，最好的 app 都是有着很多的自定义的样式风格、主题，我
们也想和那些 app 一样能够很简单的在我们的 app 中自定义样式，打造自己的品牌风格。

我们主题化 ionic app 比以前更加容易了。Ionic 是以 Sass 作为基础，Sass 允许我们为我们
的 app 设置一些默认的样式，并且改变我们默认的主题是非常容易的。

### 二、主题化 Ionic Apps ###
在你的 Ionic app 中，为了改变主题，只要在 `src/theme/variables.scss` 文件中修
改 `$color  map`：
    
    $colors: (
      primary: #387ef5,
      secondary: #32db64,
      danger: #f53d3d,
      light: #f4f4f4,
      dark: #222,
    );

改变你的 Ionic app 主题的最快方法是给  primary  设置一个新的值，因为 Ionic 的按钮和其他
的组件默认使用 primary 颜色。

#### 自定义颜色 ####
添加自定义颜色，只要添加它们（颜色）到  `$colors  map`：

    $colors: (
      // ...
      twitter: #55acee
    )
你可以使用  `base`  和  `contrast`  属性进一步自定义：

    $colors: (
      // ...
      twitter:(
        base: #55acee,
        contrast: #ffffff
      )
    )
base 为背景颜色，contrast 为文本颜色。这种进一步的自定义颜色对于控制你的样式更加灵活了。

Ionic 使用  `$colors`  中的键作为很多组件的属性是可用的。例如，使用我们上面定义的
`twitter`  颜色，让  `twitter`  作为 html 中的属性添加进去：

    <button ion-button color="twitter">I'm a button</button>

对于任何自定义的组件，你可以使用  color  函数获得正确的颜色：

    my-component {
      background: color($colors, twitter, base)
    }
color 函数将会基于 map 来查找正确的颜色，上面这种情况将会编译输出为：

    my-component {
      background: #55acee
    }

### 三、Sass 变量 ###
Sass 变量允许你定义一次变量在很多的地方使用。Sass 变量以  $  符号开始并且设置的变量
就像 CSS 属性。你可以在一个地方改变这个变量的值，并且改变之后所有的实例使用的变量
的值也是改变之后的。例如，如果你想对两个不同的选择器设置同样的高度，你可以创建一
个叫  `$control-height`  的变量：

    $control-height: 40px;
然后，你可以在多个地方使用这个变量。

    .header {
      height: $control-height;
    }
    .sub-header {
      height: $control-height;
    }
当编译成 CSS 时，上面的代码会变成这样：

    .header {
      height: 40px;
    }
      .sub-header {
      .height: 40px;
    }
如果你决定以后你想改变 $control-height 的值，这将会非常有用。并且这个可以用在不同的
选择器上。你将不再自己过滤筛选你的代码并且改写每一处的样式，而是只要更新一下
`$control-height`  变量的值就行。

Sass 和 Ionic 形影相随。使用一些 CSS 框架，你为了改变你 app 的样式，就必须创建新的
样式表并且覆盖它们的样式。在 Ionic 中，你可以直接修改 Sass 变量，以便生成你想要的自
定义的 CSS 文件。

在下一个环节，我们将学习为了获得自定义的样式，该如何覆盖 Ionic 的Sass 变量的值。

### 四、重写 Ionic Sass 变量 ###
在 Ionic 中，有很多的 变量你可以重写。下面的任何一个变量都可以在
`src/theme/variables.scss`  文件中重写，仅仅只要在这个文件中添加一个新的值：

    $text-color: #000099;
    $colors(
      ...
    )
更多变量请访问[官网](http://ionicframework.com/docs/theming/overriding-ionic-variables/)。

### 五、实用的属性 ###
Ionic 提供了一组 SCSS/CSS 实用的属性。当我们开发 app 时，可以帮助我们。

文本转换

|属性| 描述|
|:------------- |:-------------|
| text-left |文本左对齐|
| text-center | 文本居中对齐 |
| text-right | 文本右对齐 |
| text-justify | 齐行改变文字间的间隔？ |
| text-wrap | 文本超出换行 |
| text-nowrap | 文本超出不换行 |
| text-uppercase | 转换文本为大写 |
| text-lowercase | 转换文本为小写 |
| text-capitalize | 将首字母转换为大写 |

元素 Padding

|属性|描述|
|:------------- |:-------------|
| padding |为整个元素添加padding|
| padding-top |添加padding-top|
| padding-left |添加padding-left|
| padding-right |添加padding-right|
| padding-buttom |添加padding-buttom|
| padding-vertical |添加 top 和 buttom（padding）|
| padding-horizontal  |添加 left 和 right（padding）|
| no-padding  |移除所有的padding|

元素 Margin

|属性|描述|
|:------------- |:-------------|
| margin |为整个元素添加margin|
| margin-top |添加margin-top|
| margin-left |添加margin-left|
| margin-right |添加margin-right|
| margin-buttom |添加margin-buttom|
| margin-vertical |添加 top 和 buttom（margin）|
| margin-horizontal  |添加 left 和 right（margin）|
| no-margin  |移除所有的margin|

`ion-buttons` 中的属性

|属性| 描述|
|:------------- |:-------------|
|start| 基于平台在开始的地方对齐元素。IOS 在左边，Android 在右边。|
|end| 基于平台在尾部对齐元素。IOS 在右边，Android 仍然在右边。|
|left| 左对齐，不管是 IOS 还是 Android。|
|right| 右对齐，不管是 IOS 还是 Android。|

`ion-checkbox, ion-select, ion-toggle`  属性

|属性| 描述|
|:------------- |:-------------|
|item-left| ？|
|item-right| ？|

### 六、平台特殊的样式 ###