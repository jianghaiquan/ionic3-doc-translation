#ActionSheet
----------
一个Action Sheet 就是一个允许用户从一系列选项中选择的对话框。它出现在app的内容层之上，如果用户想要重新和app进行交互必须手动取消。危险的操作（具有破坏性的操作）在iOS中会以特别的方式展示出来。有很多可以退出Action Sheet的办法，就像轻触背景或者点击屏幕上的取消按钮。    

一个Action Sheet 是通过一个按钮数组来创建的，每一个按钮有自己的文本属性，有一个handler（事件）或者role，如果处handler返回了false那么这个action sheet就不能被关闭。一个action sheet也可以拥有题目、副标题、和一个图标。   

一个按钮的role属性也可以是销毁或者取消。没有role属性的按钮会有这个平台上的默认样式。拥有cancel属性的按钮将会被加载成为底部按钮，无论它们位于队列的哪个位置。所有的其他按钮将会被按照它们在按钮队列里的默认顺序展示。
Note：我们推荐销毁按钮一定要在按钮中的首位，让它们位于按钮顶端。另外，如果这个action sheet被通过轻触屏幕取消，那么将会启动拥有cancel属性的role的handler。  

你可以传递所有action sheet的属性在创建方法的第一个参数里：ActionSheet.create(opts)。另外action sheet的实例也有添加属性的方法，像是：setTitle()或者addButton()。

##Usage(用法)
<pre><code>	
import { ActionSheetController } from 'ionic-angular'

export class MyClass{

 constructor(public actionSheetCtrl: ActionSheetController) {}

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
       },
       {
         text: 'Archive',
         handler: () => {
           console.log('Archive clicked');
         }
       },
       {
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
</code></pre>

##实例成员
###config
###create(opts)
<table>
        <tr>
            <th>参数</th>
            <th>类型</th>
            <th>说明</th>
        </tr>
        <tr>
            <td>opts</td>
            <td>ActionSheetOptions</td>
            <td>Action sheet options</td>
        </tr>
</table>

###Advanced
####ActionSheet创建选项
<table>
        <tr>
            <th>参数</th>
            <th>类型</th>
            <th>说明</th>
        </tr>
        <tr>
            <td>title</td>
            <td>string</td>
            <td>Action sheet的题目</td>
        </tr>
        <tr>
            <td>subTitle</td>
            <td>string</td>
            <td>Action sheet的副标题</td>
        </tr>
         <tr>
            <td>cssClass</td>
            <td>string</td>
            <td>用户额外添加的样式，以空格键隔开</td>
        </tr>
        <tr>
            <td>enableBackdropDismiss</td>
            <td>boolean</td>
            <td>当用户点击背景时，Action sheet是否应该关闭</td>
        </tr>
        <tr>
            <td>buttons</td>
            <td>array<any></td>
            <td>一个要展示的按钮数组</td>
        </tr>
</table>
####ActionSheet 按钮选项
<table>
        <tr>
            <th>参数</th>
            <th>类型</th>
            <th>说明</th>
        </tr>
        <tr>
            <td>text</td>
            <td>string</td>
            <td>按钮内的文本</td>
        </tr>
        <tr>
            <td>icon</td>
            <td>icon</td>
            <td>按钮图标</td>
        </tr>
         <tr>
            <td>handler</td>
            <td>any</td>
            <td>按钮应该计算的表达式</td>
        </tr>
        <tr>
            <td>cssClass</td>
            <td>string</td>
            <td>用户额外添加的样式，以空格键隔开</td>
        </tr>
        <tr>
            <td>role</td>
            <td>string</td>
            <td>这个按钮应该如何被显示，销毁或者是取消，如果没有提供role，这个按钮就会不添加任何额外的样式展示出来</td>
        </tr>
</table>
###取消和异步导航
在Action sheet被关闭以后，这个app可能需要依据handler的逻辑跳转到另一个页面。然而，因为多重跳转在同时被平等的对待，对于导航控制器来说很难做到干净利落的去异步渲染多重动画跳转。这一点在Nav Transition Promises部分中做了更详细的解释。对于Action sheet来说，这意味着在同一导航控制器中最好在开始一个新的跳转之前等待完成action sheet的跳转。  
在下方的例子中，在按钮被点击之后，它的handler等待异步操作来完成，然后它使用pop来导航回同一栈中的上一个页面。潜在的问题是异步操作可能已经在action sheet动画完成前完成。这种情况下，最好首先确认action sheet已经完成了过渡，然后再启动下一个过渡。
<pre><code>
let actionSheet = this.actionSheetCtrl.create({
  title: 'Hello',
  buttons: [{
    text: 'Ok',
    handler: () => {
      // 当用户点击action sheet按钮的时候
      // 开始action sheet的取消过渡
      let navTransition = actionSheet.dismiss();

      // 开始异步操作
      someAsyncOperation().then(() => {
        // 一旦异步操作完成
        // 然后启动下一个导航过渡
        // 在第一个过渡已经完成了动画转换

        navTransition.then(() => {
          this.nav.pop();
        });
      });
      return false;
    }
  }]
});

actionSheet.present();
</code></pre>
标注出handler返回false很重要。一个按钮handlers特性是它们会自动关闭action sheet当它们的按钮被按下的时候，然而，我们需要更多的去控制跳转。因为handler返回了false，然后action sheet不自动关闭自己。相反的，你现在必须当action sheet结束过渡后的操控，以及在开始一个新跳转之前等待action sheet完成过渡。
###Sass 变量
[sass](http://ionicframework.com/docs/api/components/action-sheet/ActionSheetController/#sass-variables)
