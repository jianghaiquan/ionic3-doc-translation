### Grid
ionic的网格系统基于[flexbox](http://www.w3.org/TR/css3-flexbox/)，flexbox是一个css3的特性，ionic所支持的设备都支持此特性。网格由grid,rows,以及columns三部分组成。

更多信息请查看[API文档](http://ionicframework.com/docs/api/components/grid/Grid)

网格由12列组成，每列`ion-col`可单独设置尺寸，通过`col-<width>`属性。

[本例源码](https://github.com/driftyco/ionic-preview-app/tree/master/src/pages/grid)

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

通过设置`ion-<breakpoint>-<width>`属性可将一个`ion-col`分成不同的部分。

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