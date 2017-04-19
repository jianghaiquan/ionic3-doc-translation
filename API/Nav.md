# Nav 
`ion-nav`
`ion-nav`是[NavController](http://ionicframework.com/docs/api/navigation/NavController/)声明式的组件。
[点此](http://ionicframework.com/docs/api/navigation/NavController/)查看更多导航控制器的信息，如Nav或Tabs。

### 使用
你必须通过Nav控制器来加载并初始化一个root页面，使用`root`属性：
```
import { Component } from '@angular/core';
import { GettingStartedPage } from './getting-started';

@Component({
  template: `<ion-nav [root]="root"></ion-nav>`
})
class MyApp {
  root = GettingStartedPage;

  constructor(){
  }
}
```
### 实例成员
`goToRoot()`
`initPane()`
`ngAfterViewInit()`
`paneChanged()`

### 输入属性 

|属性|类型|详细|
|-----|-----|-----|
|root|`Page`|导航的根页面组件|
|rootParams|`object`|任意类型的导航参数，将传递给根页面|
|swipeBackEnabled|`boolean`|如果为真，页面将可以滑动返回|

### 相关
[导航组件文档](http://ionicframework.com/docs/components#navigation)