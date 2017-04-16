### DateTime
DateTime组件用于让用户方便的选择时间和日期。本组件和html5原生的`<input type="datetime-local">`组件很相似，但使用本组件可以更方便的显示指定格式的的时间和日期，设置日期的值也很方便。

更多信息请查看[API文档](http://ionicframework.com/docs/api/components/datetime/DateTime)。

#### 基本使用 [本例源码](https://github.com/driftyco/ionic-preview-app/tree/master/src/pages/datetime)


```
<ion-item>
  <ion-label>Start Time</ion-label>
  <ion-datetime displayFormat="h:mm A" pickerFormat="h mm A" [(ngModel)]="event.timeStarts"></ion-datetime>
</ion-item>

```