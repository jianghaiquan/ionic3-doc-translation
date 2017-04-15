### ChexkBox
checkbox是一个用来表示布尔值的输入组件。checkbox不同于html中的checkbox输入控件。然而，和其他的ionic组件类似，checkbox在不同平台上表现不同。使用`checked`属性可以设置默认值，使用`disabled`属性可以禁止用户改变checkbox的值。

更多信息请查看[API文档](http://ionicframework.com/docs/api/components/checkbox/Checkbox)。

#### 基本使用
```
<ion-item>
  <ion-label>Daenerys Targaryen</ion-label>
  <ion-checkbox color="dark" checked="true"></ion-checkbox>
</ion-item>

<ion-item>
  <ion-label>Arya Stark</ion-label>
  <ion-checkbox disabled="true"></ion-checkbox>
</ion-item>
```