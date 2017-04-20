# NavPush
`[navPush]`  
这是一个声明式指令，用于进入在当前的导航栈中进入新的页面。
## 使用

```
<button ion-button [navPush]="pushPage"></button>
```
如果要传递参数可以使用`navParams`属性：
```
<button ion-button [navPush]="pushPage" [navParams]="params">Go</button>
```

`pushPage`和`params`定义在组件中，`pushPage`是指向需要导航的组件的引用：

```
contains a reference to a component you would like to push:

import { LoginPage } from './login';

@Component({
  template: `<button ion-button [navPush]="pushPage" [navParams]="params">Go</button>`
})
class MyPage {
  constructor(){
    this.pushPage = LoginPage;
    this.params = { id: 42 };
  }
}
```

## 输入属性

|属性|类型|详细|
|-----|-----|-----|
|navParams|any|传递给到新视图的任意类型的参数|
|navPush|Page/string|组件类或者深链接的名字|

## 相关
[Navigation Component 文档](http://ionicframework.com/docs/components#navigation)   
[ NavPop API 文档](http://ionicframework.com/docs/api/components/nav/NavPop)
