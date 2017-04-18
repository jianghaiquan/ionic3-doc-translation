# ViewController #

使用当前视图（页面）的各种各样的特性和信息。

### 用法 ###

    import { Component } from '@angular/core';
    import{ ViewController } from 'ionic-angular';
    
    @Component({...})
    export class MyPage {
      constructor(public viewCtrl: ViewController) {}
    }

### 实例成员 ###

1. `componen`

2. `contentRef()` -> Returns：`ElementRef`，Returns the Content's ElementRef

3. `didEnter` 当当前组件变成活动的，可观察对象就会被订阅。Returns: Observable，返回一个可观察对象

4. `didLeave` 当当前组件变成不是活动的，可观察对就会被订阅。Returns: Observable，返回一个可观察对象

5. `dismiss(data, role, NavOptions)`