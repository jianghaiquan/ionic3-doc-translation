### FABs
FABs(Float Action Buttons)是个标准的material design风格的组件(material design即android平台的UI设计风格)，它以圆形的方式呈现系列操作。当按下的时候，它可能包含更多相关的操作，FABs就像它的名字那样悬浮在内容之上。

####基本使用 [本例源码](https://github.com/driftyco/ionic-preview-app/tree/master/src/pages/fabs)

```
<ion-content>
  <!-- Real floating action button, fixed. It will not scroll with the content -->
  <ion-fab top right edge>
    <button ion-fab mini><ion-icon name="add"></ion-icon></button>
    <ion-fab-list>
      <button ion-fab><ion-icon name="logo-facebook"></ion-icon></button>
      <button ion-fab><ion-icon name="logo-twitter"></ion-icon></button>
      <button ion-fab><ion-icon name="logo-vimeo"></ion-icon></button>
      <button ion-fab><ion-icon name="logo-googleplus"></ion-icon></button>
    </ion-fab-list>
  </ion-fab>

  <ion-fab right bottom>
    <button ion-fab color="light"><ion-icon name="arrow-dropleft"></ion-icon></button>
    <ion-fab-list side="left">
      <button ion-fab><ion-icon name="logo-facebook"></ion-icon></button>
      <button ion-fab><ion-icon name="logo-twitter"></ion-icon></button>
      <button ion-fab><ion-icon name="logo-vimeo"></ion-icon></button>
      <button ion-fab><ion-icon name="logo-googleplus"></ion-icon></button>
    </ion-fab-list>
  </ion-fab>

</ion-content>
```

更多信息请查看[API文档](http://ionicframework.com/docs/api/components/fab/FabButton/)