### Tabs（选项卡： tabs 是tab 的复数形式） ###

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

    @Component({
      templateUrl: 'build/pages/tabs/tabs.html'
    })
    export class TabsPage {
      // this tells the tabs component which Pages
      // should be each tab's root Page
      tab1Root = Page1;
      tab2Root = Page2;
      tab3Root = Page3;
      
      constructor() {

      }
    }
在 Tabs 页面中，默认的第一个 tab 将在被选中（在页面导航的最上面）。我们可以通过 `<ion-tabs>` 元素上的 `selectedIndex` 属性来改变这个默认的选项：

    <ion-tabs selectedIndex="2">
      <ion-tab [root]="tab1Root"></ion-tab>
      <ion-tab [root]="tab2Root"></ion-tab>
      <ion-tab [root]="tab3Root"></ion-tab>
    </ion-tabs>

因为索引从 0 开始，所以上面的代码将会选择第 3 个 tab 作为根页面。如果你向动态地改变它，你可以使用[属性绑定](https://angular.io/docs/ts/latest/guide/template-syntax.html#!#property-binding)。

或者，你可以获得 `Tabs` 的实例然后调用 `select()` 方法。这就需要 `<ion-tabs>` 元素要有一个 `id` 。例如，设置 `id` 的值为 `myTabs`：

    <ion-tabs #myTabs>
      <ion-tab [root]="tab1Root"></ion-tab>
      <ion-tab [root]="tab2Root"></ion-tab>
      <ion-tab [root]="tab3Root"></ion-tab>
    </ion-tabs>
然后在你的 class 中，你可以取得 `Tabs` 实例，然后调用 `select()` 方法，将选项卡的索引作为参数传递进去。
在这里，我们通过 ViewChild 取得 tabs：

    export class TabsPage {
      @ViewChild('myTabs') tabRef: Tabs;
      
      ionViewDidEnter() {
        this.tabRef.select(2);
      }
    }

你也可以在父视图（tabs）中使用 `NaController` 的实例，然后调用 `select()` 方法来切换子组件（tab）。例如，如果你有一个 `TabsPage` 组件，你可以调用下面的方法来从任何子组件切换到 `TabsRoot3`：

    switchTabs() {
      this.navCtrl.parent.select(2);
    }


### 实例的成员函数 ###
`getByIndex(index)`

| 参数 | 类型 | 详述 |
|-----|------|-----|
| index | `number`| 你想获得的tab的索引|
Returns： `Tab`

返回？

`getSelected()`

Returns： `Tab`

返回当前被选中的 tab

`ngOnDestroy()`

`previousTab(trimHistory)`

获得当前被选中的 Tab，并且这个 Tab 不是被禁用或者隐藏的。

| 参数 | 类型 | 详述 |
|-----|------|-----|
| trimHistory | `boolean`| ？ |
Returns: `Tab`

`select(tabOrIndex)`

| 参数 | 类型 | 详述 |
|-----|------|-----|
| tabOrIndex | `number or Tab`| ？ |

`viewCtrl`

### 输入属性 ###

| 参数 | 类型 | 详述 |
|-----|------|-----|
| selectedIndex | `number`| 第一次加载的时候，默认选择设置了此属性的的索引。如果索引没有提供，将会使用 0,即第一个 tab |
| tabsHighlight | `boolean`| 如果为true，在被选中的 tab 下面显示一个高亮的条 |
| tabsLayout | `string`| 设置 tabbar 的布局：`ionic-top`,`icon-left`,`icon-right`,`icon-bottom`,`icon-hide`,`title-hide` |
| tabsPlacement | `string`| 设置 tabbar 的位置：`top`,`bottom` |
### 输出事件 ###
| 参数 | 详述 |
|-----|------|
| ionChange | 当 tab 切换的时候触发 |

### Sass 变量 ###
[http://ionicframework.com/docs/api/components/tabs/Tabs/](http://ionicframework.com/docs/api/components/tabs/Tabs/)
