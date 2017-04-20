# NavParams
NavParams是页面(page)上的一个对象，为页面中的特定视图（指视图导航过程中被传递了参数的视图）存储着数据。类似Ionic1中的`$stateParams`，NavParams提供更有弹性的`get`方法。

## 使用

```
export class MyClass{
 constructor(public params: NavParams){
   // userParams is an object we have in our nav-parameters
   this.params.get('userParams');
 }
}
```

## 实例成员

`data`    
`get(parameter)`
获取当前视图的导航参数。
```
export class MyClass{
 constructor(public params: NavParams){
   // userParams is an object we have in our nav-parameters
   this.params.get('userParams');
 }
}
```
|参数|类型|详细}
|-----|-----|-----|
|paramter|string|需要获取的参数|

## 相关

[Navigation Component文档](http://ionicframework.com/docs/components#navigation)   
[NavController API文档](http://ionicframework.com/docs/api/navigation/NavController/)   
[ Nav API 文档](http://ionicframework.com/docs/api/components/nav/Nav/)    
[ NavPush ](http://ionicframework.com/docs/api/components/nav/NavPush/)    