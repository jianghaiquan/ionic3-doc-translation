### Gestures

基本的手势可以对html元素进行`tap`,`press`,`pan`,`swipe`,`rotate`,`pinch`事件的绑定来获取。

####基本使用[本例代码](https://github.com/driftyco/ionic-preview-app/tree/master/src/pages/gestures)
```

<ion-card (tap)="tapEvent($event)">
  <ion-item>
    Tapped: {{tap}} times
  </ion-item>
</ion-card>

```