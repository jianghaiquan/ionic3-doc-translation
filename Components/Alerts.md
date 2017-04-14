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

#Prompt Alerts#
Prompt用于输入数据或信息，Prompt经常被用于让用户在下一步操作前输入密码。
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

#Confirmation Alerts#
Confirmation Alerts常被用于app中在进行下一步操作之前让用户准确的确认一个选择。一个典型的例子是让用户确认是否要从地址簿中删除联系人。
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

#Radio#
Radio Alerts是 Confirmation Alert的一种，但它会让用户进行一些选择，只有一个选项能被选中。

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

#Checkbox#
Checkbox Alerts是Confirmation Alert的一种，它可提供多个选项。可被多选。
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

#Badges#
Badges是一个小组件，常被用于让用户知晓一个数值。它常被用在一个item中。
更多信息请查看API文档。
基本使用：
<ion-item>
  <ion-icon name="logo-twitter" item-left></ion-icon>
  Followers
  <ion-badge item-right>260k</ion-badge>
</ion-item>

Badges也可设置颜色属性：
<ion-badge color="secondary"></ion-badge>

#Buttons#
Buttons是贯穿整个app中的重要的交互方式，当用户点击时应该有明确的交互。Buttons可以设置图标和文字，且可以通过非常多的属性来加强。

简单来说，Buttons可用标准的<button>标签来实现，但它其实已经被ion-button指令进行了加强。

更多信息请查看API文档。

基本使用：
<button ion-button>Button</button>
color属性可以设置button的颜色，ionic内置多种默认颜色，且可以很容易的改写。
<button ion-button color="light">Light</button>
<button ion-button>Default</button>
<button ion-button color="secondary">Secondary</button>
<button ion-button color="danger">Danger</button>
<button ion-button color="dark">Dark</button>

Outline Style
要使用Outline风格的Button，秩序添加Outline属性：
<button ion-button color="light" outline>Light Outline</button>
<button ion-button outline>Primary Outline</button>
<button ion-button color="secondary" outline>Secondary Outline</button>
<button ion-button color="danger" outline>Danger Outline</button>
<button ion-button color="dark" outline>Dark Outline</button>

Clear Style
要使用Clear风格的Button，秩序添加Clear属性：
<button ion-button color="light" clear>Light Clear</button>
<button ion-button clear>Primary Clear</button>
<button ion-button color="secondary" clear>Secondary Clear</button>
<button ion-button color="danger" clear>Danger Clear</button>
<button ion-button color="dark" clear>Dark Clear</button>

Round Buttons
要创建圆角按钮，只需添加round属性：
<button ion-button color="light" round>Light Round</button>
<button ion-button round>Primary Round</button>
<button ion-button color="secondary" round>Secondary Round</button>
<button ion-button color="danger" round>Danger Round</button>
<button ion-button color="dark" round>Dark Round</button>

Block Buttons
添加block属性会使按钮宽度和其父元素相等，它会添加display:block属性到按钮上：
<button ion-button block>Block Button</button>

Full Buttons
添加full属性到一个按钮上，会使按钮达到100%其父元素的宽度。然而也会移除按钮的左右边框。当一个按钮需要横跨整个宽度的时候，可以用这个属性。
<button ion-button full>Full Button</button>

Button Sizes
添加large属性可以让一个按钮变得更大，或者添加small属性使按钮变得更小：
<button ion-button small>Small</button>
<button ion-button>Default</button>
<button ion-button large>Large</button>

Icon Buttons
为一个按钮添加图标，可以在按钮中使用icon组件，并可以设置position属性：
<!-- Float the icon left -->
<button ion-button icon-left>
  <ion-icon name="home"></ion-icon>
  Left Icon
</button>

<!-- Float the icon right -->
<button ion-button icon-right>
  Right Icon
  <ion-icon name="home"></ion-icon>
</button>

<!-- Only icon (no text) -->
<button ion-button icon-only>
  <ion-icon name="home"></ion-icon>
</button>

Buttons In Components
尽管按钮可以单独使用，但也可以很容易的在其他组件中使用，比如，按钮可以在列表的列表项中使用，或者在导航栏中使用：
<ion-header>
  <ion-navbar>
    <ion-buttons start>
      <button ion-button icon-only>
        <ion-icon name="contact"></ion-icon>
      </button>
    </ion-buttons>

    <ion-buttons end>
      <button ion-button icon-only>
        <ion-icon name="search"></ion-icon>
      </button>
    </ion-buttons>
  </ion-navbar>
</ion-header>

<ion-list>
  <ion-item>
    Left Icon Button
    <button ion-button outline item-right icon-left>
      <ion-icon name="star"></ion-icon>
      Left Icon
    </button>
  </ion-item>
</ion-list>
