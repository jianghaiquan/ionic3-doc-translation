### Grid
ionic������ϵͳ����[flexbox](http://www.w3.org/TR/css3-flexbox/)��flexbox��һ��css3�����ԣ�ionic��֧�ֵ��豸��֧�ִ����ԡ�������grid,rows,�Լ�columns��������ɡ�

������Ϣ��鿴[API�ĵ�](http://ionicframework.com/docs/api/components/grid/Grid)

������12����ɣ�ÿ��`ion-col`�ɵ������óߴ磬ͨ��`col-<width>`���ԡ�

[����Դ��](https://github.com/driftyco/ionic-preview-app/tree/master/src/pages/grid)

```
<ion-grid>
  <ion-row>
    <ion-col col-12>This column will take 12 columns</ion-col>
  </ion-row>
  <ion-row>
    <ion-col col-6>This column will take 6 columns</ion-col>
  </ion-row>
</ion-grid>
```

ͨ������`ion-<breakpoint>-<width>`���Կɽ�һ��`ion-col`�ֳɲ�ͬ�Ĳ��֡�

```
<ion-grid>
  <ion-row>
    <ion-col col-12 col-sm-9 col-md-6 col-lg-4 col-xl-3>
      This column will be 12 columns wide by default,
      9 columns at the small breakpoint,
      6 at the medium breakpoint, 4 at large, and 3 at xl.
    </ion-col>
  </ion-row>
</ion-grid>
```