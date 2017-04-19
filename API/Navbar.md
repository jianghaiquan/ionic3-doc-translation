# Navbar
`ion-navbar`
Navbar扮演导航栏的角色，自带返回按钮。一个Navbar可包含一个`ion-title`，许多的按钮，或者一个搜索栏。Navbar必须被放在`ion-header`中，以便它能够放到`ion-content`的上面。需要注意的是Navbar是动态导航栈的一部分，如果你需要一个静态的工具栏，请使用`ion-toolbar`。

### 使用
```
<ion-header>

  <ion-navbar>
    <button ion-button icon-only menuToggle>
      <ion-icon name="menu"></ion-icon>
    </button>

    <ion-title>
      Page Title
    </ion-title>

    <ion-buttons end>
      <button ion-button icon-only (click)="openModal()">
        <ion-icon name="options"></ion-icon>
      </button>
    </ion-buttons>
  </ion-navbar>

</ion-header>
```

### 实例成员

`backButtonClick()`
` setBackButtonText()`
用于设置返回按钮的文字，默认是"back"。

### 输入属性

|属性|类型|详细|
|-----|-----|-----|
|hideBackButton|`boolean`|如果为真，返回按钮将被隐藏|

### 相关
[Toolbar API文档](http://ionicframework.com/docs/api/components/toolbar/Toolbar/)