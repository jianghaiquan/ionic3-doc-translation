### DateTime
DateTime����������û������ѡ��ʱ������ڡ��������html5ԭ����`<input type="datetime-local">`��������ƣ���ʹ�ñ�������Ը��������ʾָ����ʽ�ĵ�ʱ������ڣ��������ڵ�ֵҲ�ܷ��㡣

������Ϣ��鿴[API�ĵ�](http://ionicframework.com/docs/api/components/datetime/DateTime)��

#### ����ʹ�� [����Դ��](https://github.com/driftyco/ionic-preview-app/tree/master/src/pages/datetime)


```
<ion-item>
  <ion-label>Start Time</ion-label>
  <ion-datetime displayFormat="h:mm A" pickerFormat="h mm A" [(ngModel)]="event.timeStarts"></ion-datetime>
</ion-item>

```