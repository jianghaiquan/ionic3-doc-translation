# 迁移概念

Ionic是构建在Angular之上的，它完全重写了原来的框架。你知道的所有关于Angular的部分仍然不变。但是会有需要开发者注意的新语法和结构上的改变。对于Angular的改变概览，可以看看[学习Angular文档](http://learnangular2.com/)

在Ionic中，我们会觉得很熟悉。所有来自Ionic Vv1的概念仍然在最新版本中。虽然塔门可能看起来有些许不同，你仍然又像你在v2中的视图和控制器。但是它们被合并进了一个实例。

 举一个v1例子：

v1

```
.config(function($stateProvider){
  $stateProvider
  .state('main', {
    url: '/',
    templateUrl: 'templates/main.html',
    controller: 'MainCtrl'
  })
})

.controller('MainCtrl', function(){

})
```

你可以像这样重写来使用最新的Ionic:

```
@Component({
  templateUrl:'main/main.html'
})
export class MainCmp {
  constructor() {

  }
}
```

像导航这样其他的变化，虽然有很大的不同，但我们保证是好的原因。现在你可以像任意视图一样对待组件并且导航到任何你想去的地方。这会使得导航更灵活切允许更原生风格的导航堆栈。



## 从Angular1的迁移

当Angular2要求应用程序为了语法变化而更新的时候，开发者可能会积极主动而且通过[John Papa的Angula风格引导](https://github.com/johnpapa/angular-styleguide)或者[Todd Motto的Angular风格引导](https://github.com/toddmotto/angularjs-styleguide)的实践和工作来确保他们的应用程序是升级版。这些都会提供你可以采取的步骤来准备迁移代码。

### 控制器语法

控制器语法是Angular1.x的特性，你可以绑定控制器的直接实例而不是绑定数据到$scope。这会是的迁移一个Angular 1.x控制器到Angular 2.x控制器变得简单很多。从传统控制器迁移到新控制器是非常简单的：

index.html

```
   <ion-content ng-controller="MainCtrl">
      <ion-item>
        {{data.text}}
      </ion-item>
    </ion-content>

```

app.js

```
    .controller('MainCtrl', function($scope){
      $scope.data ={
        text: 'Hello World'
      }
    })
```

为了转换成控制器语法，你只能改变一些东西。

index.html

```
    <ion-content ng-controller="MainCtrl as main">
      <ion-item>
        {{main.data.text}}
      </ion-item>
    </ion-content>
```

app.js

```
    .controller('MainCtrl', function(){
      this.data ={
        text: 'Hello World'
      }
    })
```

### TypeScript

TypeScript是在你的代码中提供ES6语法和注释类型的JavaScript的超集。现在采用TypeScript，你可以编写代码为6类，可以很容易地转移到Ionic。最好的地方是，任何有效的JavaScript也是有效的TypeScript，所以你可以将你的代码片段。如果你把你的控制器之前，你可以很容易地将它转换成一个TypeScript就像这样：

app.js

```
    .controller('MainCtrl', function(){
      this.data ={
        text: 'Hello World'
      }
    })
```

app.ts

```
    export class MainCtrl{
      constructor(){
        this.data ={
          text: 'Hello World'
        }
      }
    }
```

### 项目结构

在Angular1中，这是一个让所有的JavaScript和你的模板分开的实践，。由于Ionic和angular2将移动到组件库设置，您可以重新部署您的项目，以帮助精神上执行这个概念。所以一个项目的目录看起来像这样…

```
    |-www/
    |
    |--js/
    |--|-app.js
    |--|-HomeCtrl.js
    |--|-DetailCtrl.js
    |
    |--templates/
    |--|-Home.html
    |--|-Detail.html
    |
    |-index.html
```

可以像这样初始化

```
    |-www/
    |
    |--Home/
    |--|-HomeCtrl.js
    |--|-Home.html
    |
    |--Detail/
    |--|-DetailCtrl.js
    |--|-Detail.html
    |
    |-index.html
    |-app.js
```

像这样初始化你的项目能够在心态上帮助你认识到你的应用程序的视图是一个带有一个模板和一个控制器的组件。



