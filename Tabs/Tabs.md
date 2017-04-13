### Tabs（选项卡） ###

----------
#### `ion-tabs` ####

在一个 app 中，Tabs 使得在不同页面和功能之间导航更加容易。Tabs 组件，以 `<ion-tabs>` 的方式写，是单个 Tab 组件的容器。每个 `<ion-tab>` 对于 NavControll 来说是公开的组件

更多使用 导航控制器 （Tab或者Nav），请看 NavController API 文档。

#### 位置 ####

tabs 的位置与基于风格（android、ios）的内容变化有关。tabs 在 IOS 和 Android 中被放置在屏幕的底部，对于 Windows，默认得在顶部。可以在 `ion-tabs` 中使用 `tabsPlacement` 属性来配置 tabs 的位置，或者在 app 的 [config](http://ionicframework.com/docs/api/config/Config/)中配置。可以在下方（本节）看到 `tabsPlacement` 的[输入属性](http://ionicframework.com/docs/api/components/tabs/Tabs/#input-properties)。

### 布局 ###
就 tabs 的布局来说，可以使用 `tabsLayout` 属性。如果单个的 tab 有标题和图标，默认地，图标会展示在标题的上方。通过在 `<ion-tabs>` 上设置 `tabsLayout` 的值，所有的 tab 都会改变（布局），或者改变你 app 的[配置](http://ionicframework.com/docs/api/config/Config/)。例如，如果你想在 Android 上只有标题，但是在 IOS 上有标题和图标，这很有用~在下方（本节）可以看到 `tabsLayout` 的输入属性。

### 选择一个tab ###
从 tabs 组件中选择一个特定的 tab 有几种不同的方法。在你可以在 `<ion-tabs>` 上使用 `selectedIndex` 属性设置索引来选择一个 tab，或者你可以在创建了 `Tab` 实例之后，调用 `select()` 方法。更多信息，请看下面的用法。

### 用法 ###
你可以添加下面的模板：

    <ion-tabs>
      <ion-tab [root]="tab1Root"></ion-tab>
      <ion-tab [root]="tab2Root"></ion-tab>
      <ion-tab [root]="tab3Root"></ion-tab>
    </ion-tabs>
`tab1Root`，`tab2Root`，`tab3Root` 是每一个页面：
