### Action Sheets

Action Sheets从设备屏幕底部边缘滑上来，显示一些有确认或取消功能的选项。Action Sheets可用来替代菜单，然后不要将它们作为导航使用。

ActionSheets总是出现在页面中其他组件之上，并且必须被隐藏掉以便用户能和它下面的内容交互。当ActionSheets出现的时候页面整体变暗，以便突出ActionSheets。

更多信息请查看API文档。

### 基本使用
```
import { ActionSheetController } from 'ionic-angular';

export class MyPage {
  constructor(public actionSheetCtrl: ActionSheetController) {
  }

  presentActionSheet() {
    let actionSheet = this.actionSheetCtrl.create({
      title: 'Modify your album',
      buttons: [
        {
          text: 'Destructive',
          role: 'destructive',
          handler: () => {
            console.log('Destructive clicked');
          }
        },{
          text: 'Archive',
          handler: () => {
            console.log('Archive clicked');
          }
        },{
          text: 'Cancel',
          role: 'cancel',
          handler: () => {
            console.log('Cancel clicked');
          }
        }
      ]
    });
    actionSheet.present();
  }
}
```