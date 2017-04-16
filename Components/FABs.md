### FABs
FABs(Float Action Buttons)�Ǹ���׼��material design�������(material design��androidƽ̨��UI��Ʒ��)������Բ�εķ�ʽ����ϵ�в����������µ�ʱ�������ܰ���������صĲ�����FABs��������������������������֮�ϡ�

####����ʹ�� [����Դ��](https://github.com/driftyco/ionic-preview-app/tree/master/src/pages/fabs)

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

������Ϣ��鿴[API�ĵ�](http://ionicframework.com/docs/api/components/fab/FabButton/)