### Alerts
如果要让用户选择一个操作或者从一列操作，Alerts是一种非常好的方式。它可以为用户提供重要的信息，或者要求用户做一个选择（或者多选）。

从UI的角度来说，Alerts可以想象为覆盖在屏幕上一部分的“漂浮”对话框，这意味着Alerts不应该被用做一个非常快速的操作比如密码验证，小的app提醒，或者快速选择。更深的用户交互应该使用全屏的Modals。

Alerts非常灵活且易于定制。

更多信息请查看API文档。

### 基本使用
基本的Alerts通常被用于提醒用户新的信息（比如app中的变化，新的特性等），让用户知道某个紧急情况，或者提醒用户某个操作的成功与否。

```
import { AlertController } from 'ionic-angular';

export class MyPage {
  constructor(public alertCtrl: AlertController) {
  }

  showAlert() {
    let alert = this.alertCtrl.create({
      title: 'New Friend!',
      subTitle: 'Your friend, Obi wan Kenobi, just accepted your friend request!',
      buttons: ['OK']
    });
    alert.present();
  }
}
```

### Prompt Alerts
Prompt用于输入数据或信息，Prompt经常被用于让用户在下一步操作前输入密码。
```
import { AlertController } from 'ionic-angular';

export class MyPage {
  constructor(public alertCtrl: AlertController) {
  }

  showPrompt() {
    let prompt = this.alertCtrl.create({
      title: 'Login',
      message: "Enter a name for this new album you're so keen on adding",
      inputs: [
        {
          name: 'title',
          placeholder: 'Title'
        },
      ],
      buttons: [
        {
          text: 'Cancel',
          handler: data => {
            console.log('Cancel clicked');
          }
        },
        {
          text: 'Save',
          handler: data => {
            console.log('Saved clicked');
          }
        }
      ]
    });
    prompt.present();
  }
}
```
### Confirmation Alerts
Confirmation Alerts常被用于app中在进行下一步操作之前让用户准确的确认一个选择。一个典型的例子是让用户确认是否要从地址簿中删除联系人。
```
import { AlertController } from 'ionic-angular';

export class MyPage {
  constructor(public alertCtrl: AlertController) {
  }

  showConfirm() {
    let confirm = this.alertCtrl.create({
      title: 'Use this lightsaber?',
      message: 'Do you agree to use this lightsaber to do good across the intergalactic galaxy?',
      buttons: [
        {
          text: 'Disagree',
          handler: () => {
            console.log('Disagree clicked');
          }
        },
        {
          text: 'Agree',
          handler: () => {
            console.log('Agree clicked');
          }
        }
      ]
    });
    confirm.present();
  }
}
```
#Radio#
Radio Alerts是 Confirmation Alert的一种，但它会让用户进行一些选择，只有一个选项能被选中。
```
import { AlertController } from 'ionic-angular';

export class MyPage {
  constructor(public alertCtrl: AlertController) {
  }

  showRadio() {
    let alert = this.alertCtrl.create();
    alert.setTitle('Lightsaber color');

    alert.addInput({
      type: 'radio',
      label: 'Blue',
      value: 'blue',
      checked: true
    });

    alert.addButton('Cancel');
    alert.addButton({
      text: 'OK',
      handler: data => {
        this.testRadioOpen = false;
        this.testRadioResult = data;
      }
    });
    alert.present();
  }
}
```
### Checkbox
Checkbox Alerts是Confirmation Alert的一种，它可提供多个选项。可被多选。
```
import { AlertController } from 'ionic-angular';

export class MyPage {
  constructor(public alertCtrl: AlertController) {
  }

  showCheckbox() {
    let alert = this.alertCtrl.create();
    alert.setTitle('Which planets have you visited?');

    alert.addInput({
      type: 'checkbox',
      label: 'Alderaan',
      value: 'value1',
      checked: true
    });

    alert.addInput({
      type: 'checkbox',
      label: 'Bespin',
      value: 'value2'
    });

    alert.addButton('Cancel');
    alert.addButton({
      text: 'Okay',
      handler: data => {
        console.log('Checkbox data:', data);
        this.testCheckboxOpen = false;
        this.testCheckboxResult = data;
      }
    });
    alert.present();
  }
}
```