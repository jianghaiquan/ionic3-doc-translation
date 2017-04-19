# NavController
NavController是导航控制器组件类如`Nav`和`Tab`类的基类（父类）。我们使用导航控制器实现在app中页面的导航，简单来说，导航控制器是一些页面组成的数组，代表特定的页面历史记录，比如一个Tab页的历史记录。它可以控制app的页面导航，通过弹入弹出页面，也可以从历史记录的任意位置插入或移除页面。

当前页面是页面数组中的最后一个，也可以认为是历史堆栈的顶部页面。`Push`一个页面到导航栈中，这个页面将被动态载入。`pop`当前页面将会导航到上一个页面。

大多数时候我们使用最近使用的`NavController`的引用来导航页面，你也可以使用`NavPush`指令或者指定的导航控制器来导航页面。

## 基本使用
在app中进行页面间导航最简单的方法是创建并初始化一个新的导航控制器使用`<ion-nav>`组件，`ion-nav`继承自`NavController`类。

```
import { Component } from `@angular/core`;
import { StartPage } from './start-page';

@Component(
  template: `<ion-nav [root]="rootPage"></ion-nav>`
})
class MyApp {
  // set the rootPage to the first page we want displayed
  public rootPage: any = StartPage;

  constructor(){
  }
}
```
## 注入导航控制器
通过注入的方式获取的导航控制器是最近使用的一个导航控制器实例，不管是在普通导航中还是在tab导航中。

这是因为，当ionic创建导航控制器的时候，它是通过注解的方式创建一个注入器，同时创建导航控制器的。同时ionic将这个注入器加入到它的自己的providers中。更多关于providers和依赖注入的信息请查看[依赖注入](https://angular.io/docs/ts/latest/guide/dependency-injection.html)（Ionic依赖注入中的对象是单例模式的，在注入对象的时候先检查是否已经有该对象的实例，如果没有就创建一个，如果有就直接注入，所以上文说“会使用最近使用的一个导航控制器实例”）。

### 栗子：
```
import { NavController } from 'ionic-angular';

class MyComponent {
  constructor(public navCtrl: NavController) {

  }
}
```

## 从根组件开始导航
如果想要从根组件开始导航该怎么做呢？在根组件中无法注入`NavController`，因为所有导航控制器的组件都是根组件的子组件，所以它们无法被注入（在根组件中，子组件还未初始化/实例化，所以无法获取它们的导航控制器）。
我们可以使用`@ViewChild`注解来获取根组件的`Nav`组件的实例的引用，它是一个导航控制器的实例（继承自`NavController`）。

```
import { Component, ViewChild } from '@angular/core';
import { NavController } from 'ionic-angular';

@Component({
   template: '<ion-nav #myNav [root]="rootPage"></ion-nav>'
})
export class MyApp {
   @ViewChild('myNav') nav: NavController
   public rootPage = TabsPage;

   // Wait for the components in MyApp's template to be initialized
   // In this case, we are waiting for the Nav with reference variable of "#myNav"
   ngOnInit() {
      // Let's navigate from TabsPage to Page1
      this.nav.push(Page1);
   }
}
```

### 从遮罩类型的组件中导航
如果想要从popover,model,alert这类遮罩的组件中导航该怎么办呢？下面的例子中我们在app中弹出一个popover，在popover中我们用`getRootNav()`方法获取根组件的`NavController`引用。

```
import { Component } from '@angular/core';
import { App, ViewController } from 'ionic-angular';

@Component({
    template: `
    <ion-content>
      <h1>My PopoverPage</h1>
      <button ion-button (click)="pushPage()">Call pushPage</button>
     </ion-content>
    `
  })
  class PopoverPage {
    constructor(
      public viewCtrl: ViewController
      public appCtrl: App
    ) {}

    pushPage() {
      this.viewCtrl.dismiss();
      this.appCtrl.getRootNav().push(SecondPage);
    }
  }
```
## 视图创建
当视图被加入到导航栈的时候会被创建，通过`push`等方法。NavController的第一个参数是任意一个被`@Component`装饰的组件类，然后NavController编译组件，将它以动画的形式载入app中。
默认情况下，当导航到新页面时，导航栈中的其他页面会被缓存在DOM中（比如通过push方法导航到新页面）。当调用`pop()`或`setRoot()`方法时页面将被销毁。

## 压入视图
要想向导航栈中加入新的页面请使用`push()`方法，如果新加入的页面中有`<ion-navbar>`，它将会带一个返回按钮。

通过`push()`方法也可以传递任意类型数据到新页面，新页面通过`NavParams`类获取数据。

```
import { Component } from '@angular/core';
import { NavController } from 'ionic-angular';
import { OtherPage } from './other-page';
@Component({
   template: `
   <ion-header>
     <ion-navbar>
       <ion-title>Login</ion-title>
     </ion-navbar>
   </ion-header>

   <ion-content>
     <button ion-button (click)="pushPage()">
       Go to OtherPage
     </button>
   </ion-content>
   `
})
export class StartPage {
  constructor(public navCtrl: NavController) {
  }

  pushPage(){
    // push another page onto the navigation stack
    // causing the nav controller to transition to the new page
    // optional data can also be passed to the pushed page.
    this.navCtrl.push(OtherPage, {
      id: "123",
      name: "Carl"
    });
  }
}

import { NavParams } from 'ionic-angular';

@Component({
  template: `
  <ion-header>
    <ion-navbar>
      <ion-title>Other Page</ion-title>
    </ion-navbar>
  </ion-header>
  <ion-content>I'm the other page!</ion-content>`
})
class OtherPage {
  constructor(private navParams: NavParams) {
     let id = navParams.get('id');
     let name = navParams.get('name');
  }
}
```

## 移除视图
移除视图请使用`pop`方法，移除一个视图后将回退到前一个视图。

```
import { Component } from '@angular/core';
import { NavController } from 'ionic-angular';

@Component({
  template: `
  <ion-header>
    <ion-navbar>
      <ion-title>Other Page</ion-title>
    </ion-navbar>
  </ion-header>
  <ion-content>I'm the other page!</ion-content>`
})
class OtherPage {
   constructor(public navCtrl: NavController ){
   }

   popView(){
     this.navCtrl.pop();
   }
}
```

## 生命周期事件
生命周期事件在导航的多个步骤中都会触发。它们可以定义在任意组件类中。

```
import { Component } from '@angular/core';

@Component({
  template: 'Hello World'
})
class HelloWorld {
  ionViewDidLoad() {
    console.log("I'm alive!");
  }
  ionViewWillLeave() {
    console.log("Looks like I'm about to leave :(");
  }
}
```
|事件类型|返回值|说明|
|-----|-----|-----|
|ionViewDidLoad|void|页面加载完成时触发。如果页面是被缓存的，那么当再次来到该页面时将不会触发本事件。在本事件中可以对页面进行进本的设置|
|ionViewWillEnter|void|即将进入页面且页面将被激活时触发|
|ionViewDidEnter|void|完全进入页面且页面已被激活时触发。不管是首次载入页面或是从缓存中载入页面，本方法都会触发|
|ionViewWillLeave|void|即将离开页面，页面将变为非激活状态时触发|
|ionViewDidLeave|void|已经离开页面，页面已经变为非激活状态时触发|
|ionViewWillUnload|void|页面将被销毁，dom元素将被移除时触发|
|ionViewCanEnter|boolean/Promise<void>|在页面可以被进入前触发。在需要权限才能查看的页面，本方法可以作为一种“守卫”方式|
|ionViewCanLeave|boolan/Promise<void>|在页面可以离开前触发。在需要权限才能离开的页面，本方法可以作为一种“守卫”方式|

## 导航守护（Nav Guards)

某些情况下开发者需要控制页面的去留。为实现这种情况，NavController有`ionViewCanEnter`和`ionViewCanLeave`方法。和angular2的路由守卫类似，但和NavController更加紧密结合在一起。比如说，如果想要阻止用户离开一个页面：

```
export class MyClass{
 constructor(
   public navCtrl: NavController
  ){}

  pushPage(){
    this.navCtrl.push(DetailPage)
     .catch(()=> console.log('should I stay or should I go now'))
  }

  ionViewCanLeave(): boolean{
   // here we can either return true or false
   // depending on if we want to leave this view
   if(isValid(randomValue)){
      return true;
    } else {
      return false;
    }
  }
}
```
需要确保`NavCtrl.push`进行了异常捕获，以便处理。类似的，如果要阻止一个页面被载入：
```
export class MyClass{
 constructor(
   public navCtrl: NavController
  ){}

  pushPage(){
    this.navCtrl.push(DetailPage)
     .catch(()=> console.log('should I stay or should I go now'))
  }

}

export class DetailPage(){
  constructor(
    public navCtrl: NavController
  ){}
  ionViewCanEnter(): boolean{
   // here we can either return true or false
   // depending on if we want to leave this view
   if(isValid(randomValue)){
      return true;
    } else {
      return false;
    }
  }
}
```
和上面类似我们仍需要捕获异常妥善处理。对于导航栏中的返回按钮，ionic框架已经进行了异常处理。

## NavOptions
`NavController`的一些方法可以定制转场动画。我们通过修改对象的属性并传递这个对象来实现。
|属性|值类型|描述|
|-----|-----|-----|
|animate|boolean|是否显示动画|
|animation|string|动画类型|
|direction|string|动画方向，比如`forword`,`back`|
|duration|number|动画时长|
|easing|string|函数动画|

`animation`属性的可选值：`md-transition`,`ios-transition`,`wp-transition`.

## 实例成员

`canGoBack()`
是否可返回
返回：`boolean`

`canSwipeBack()`
是否可以滑动返回。如果不能滑动返回或滑动返回被禁用，返回false。
返回值：`boolean`

`first()`
返回导航栈的第一个视图
返回值：`ViewController`

`getActive()`
返回当前激活的视图
返回值：`ViewControler`

`getActiveChildNav()`
返回激活的子导航

`getByIndex(index)`
返回导航栈中指定的视图
返回值：`ViewController`

`getPrevious(view)`
返回上一个视图，如果没有上一个那么返回当前激活的视图
返回值：`ViewController`

`getViews()`
返回当前导航控制器中的视图
返回值：`Array<ViewController>

`indexOf(view)`
返回指定视图在导航栈中的序号
返回值：`number`

`insert(insertIndex,page,params`,opts)`
在导航栈指定位置插入视图

|参数|类型|详细|
|-----|-----|-----|
|insertIndex|number|要插入的位置|
|page|Page/string|组件名或深链接名|
|params|object|传递给插入页面的参数(可选)|
|opts|object|导航参数（可选）|

返回值：`Promise`
返回的promise当页面动画完成时触发resolvd方法。

`isActive(view)`
给定视图是否激活
返回值：`boolean`

`isTransition()`
导航控制器是否正在进行转场动画
返回值：`boolean`

`last()`
返回导航栈的最后一个视图
返回值：`ViewController`

`length()`
导航栈中视图数量
返回值：`number`
返回导航栈中视图的数量包括当前视图

`parent`
父视图的导航控制器实例。如果当前是根视图则返回null。当前是tab则返回tabs，其他情况如果不是根视图则返回其他的导航控制器。

`pop(opts)`
从当前视图返回。和push方法类似，也可以传递可选的导航参数。
返回值：`promise`
返回的promise在转场动画完成后调用resolved方法。

`popToRoot(opts)`
返回到根视图
返回值：`Promise`
返回的Promise当转场动画完成时触发resolved方法。

`remove(startindex,removeCount,opts)`
从导航栈的指定位置移除指定数量的视图。
返回值：`Promise`

`removeView(viewController,opts)`
移除指定视图
返回值：`promsie`

`setPages(pages,opts)
设置当前导航栈的全部视图且导航到最后的视图。默认动画关闭，可以传递参数来打开。也可以传递参数到视图。
|参数|类型|详细|
|-----|-----|-----|
|pages|Array<{page:any,params:any}>|包含视图和参数的对象数组|
|opts|Object|可选的转场动画参数|
返回值：`Promise`

`setRoot(page,params,opts)`
设置根视图
|参数|类型|详细|
|page|Page/string/ViewController|想要压入导航栈的视图名|
|params|object|导航参数，可选|
|opts|object|转场动画参数|

返回值：`Promise`

`ViewDidEnter`
视图完全激活时触发
返回值：`Observable`

`viewDidLeave`
完全离开视图时触发

`viewDidLoad`
视图载入完成时触发

`viewWillEnrer`
视图即将进入开触发

`viewWillLeave`
视图即将离开触发

`viewWillUnload`
视图即将销毁触发

## 相关

[导航组件文档](http://ionicframework.com/docs/components#navigation)