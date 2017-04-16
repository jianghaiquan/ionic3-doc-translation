 `ion-tab`

Tab 组件，写作 `<ion-tab>` ，样式是以风格（IOS、Androd）为依据，并且和 Tabs 组件协作。

每个 `ion-tab`  is a declarative component for a NavController（导航控制器）。从根本上说，每个 tab 是一个 `NaController`。为了获得更多的使用导航控制器的使用方法，请看 [NavController API Docs](http://ionicframework.com/docs/api/navigation/NavController/)。

查看 [Tabs API Docs](http://ionicframework.com/docs/api/components/tabs/Tabs/)获得更加详细的 Tabs 配置。

#### 用法 ####

为了添加一个基本的 tab，你可以使用下面的标签，在那个标签上，有一个 `root` 属性，这个属性表示你想要加载的的那个 tab。`tabTitle` 是一个可选的文本属性，`tabIcon` 是可选的 [icon（图标）](http://ionicframework.com/docs/api/components/icon/Icon/)：

    <ion-tabs>
      <ion-tab [root]="chatRoot" tabTitle="Chat" tabIcon="chat"></ion-tab>
    </ion-tabs>

然后，你可以导入一个类，并且设置 `chatRoot` 为你导入的那个类：

    import { ChatPage } from '../chat/chat';
    
    export class Tabs {
      // 下面，我们将会设置 chatRoot 的属性值为我们上面导入的那个类
      chatRoot = ChatPage;

      constructor() {

      }
    }

你也可以通过`rootParams` 属性来传递一些参数到 tab 的根页面。下面，我们传递 `chatParams` 到 Chat tab：

    <ion-tabs>
      <ion-tab [root]="chatRoot" [rootParams]="chatParams" tabTitle="Chat" tabIcon="chat"></ion-tab>
    </ion-tabs>
    ...
    export class Tabs {
      chatRoot = ChatPage;
      
      // 在chatparams 对上设置一些用户的信息
      chatParams = {
        user1: 'admin',
        user2: 'ionic'
      };

      constructor() {
      
      }
    }

并且，在 `ChatPage` 中，你可以从 `NavParams` 中获得数据：

    export class ChatPage {
      constructor(naParams: NavParams) {
        console.log('Passed params', navParams.data);
      }
    }

有时，你可能想要调用一个方法来代替导航到一个新的页面。当其中的一个 tab 已经被选中的时候，你可以在你的类中，使用 `ionSelect` 事件来调用方法。下面是一个例子：

    <ion-tabs>
      <ion-tab (ionSelect)="chat()" tabTitle="Show Modal"></ion-tab>
    </ion-tabs>
    ...
    export class Tabs {
      constructor(public modalCtrl: ModalController) {}
      
      chat() {
          let modal = this.modalCtrl.create(ChatPage);
          modal.presend();
      }
    }

#### 输入属性 ####

| 属性 | 类型 | 详述 |
|-----|------|-----|
| enabled | `boolean` | 如果为true，tab 有效。如果为false，用户就不能与这个元素交互。默认值：`true` |
| root | `Page` | 为这个 tab 设置根页面 |
| rootParams | `object` | 任何的传递到这个 tab 的根页面的参数 |
| show | `boolean` | 如果为true，tab 按钮在 tab 条中是可见的。默认值：true |
| swipeBackEnabled | `boolean` | 如果为true，swipe to go back is enabled. |
| tabBadge | `string` | 设置 tab 按钮的徽章 |
| tabBadgeStyle | `string` | 设置 tab 按钮徽章的颜色 |
| tabIcon | `string` | 设置 tab 按钮的图标 |
| tabTitle | `string` | 设置 tab 按钮的标题 |
| tabUrlPath | `string` | The URL path name to represent this tab within the URL. |
| tabsHideOnSubpages | `boolean` | 如果为true，在子页面的隐藏 tabs |

#### 事件 ####

| 属性 | 详述 |
|-----|------|
| ionSelect | tab 被选中时触发 |

#### Sass 变量 ####
[http://ionicframework.com/docs/api/components/tabs/Tab/](http://ionicframework.com/docs/api/components/tabs/Tab/)