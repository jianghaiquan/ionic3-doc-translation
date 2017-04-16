#AlertController
------------------
一个警示框就是一个提供给用户一些信息或者通过用户点击提交收集信息的对话框。警示框出现在app的内容层之上。它也可以拥有（视情况）题目、副标题和信息。   

你可以通过传递所有警示框的属性给创建方法**create(opts)**的第一个形参。另外，警示框的实例也有添加属性的方法，像**setTitle()**或者**addButton()**。
##Alert Buttons
在按钮数组中，每一个按钮都有文本属性，也有可能有一个handler（事件处理器）。如果一个handler返回了false，那么当这个按钮被点击的时候，警示框不会自动消失。所有的按钮都会按照它们被添加到按钮数组里的顺序展示出来，从左到右。
小贴士：最右边的按钮（按钮数组的最后一个）是主按钮。

role属性也可以根据需求加入到按钮里，像是cancel。如果一个cancel role是按钮数组里其中的一个，那么如果警示框被轻触背景关闭的话，就会触发这个有cancel role的handler。
##Alert Inputs
警示框也可以拥有多个不同的提交框（数据可以返回到app中）。提交框可以被作为一种提示用户（请求）输入信息的方式。单选框，复选框和文字输入框都是可以应用的，但是它们不能同时混合应用。举个例子，一个警示框可以拥有所有的单选钮，或者是多选按钮，但是相同的警示框不能同时拥有（混合）多选框和单选框。然而有一点不得不提，不同类型的文字输入框可以被同时（混合）使用，就像是url，email，text等等。如果你需要一个复杂的表格UI以至于不是很符合警示框的标准，那么我们推荐你去搭建一个拥有表单的模块。
##用法
-------------------------
<pre>
	<code>
		constructor(private alertCtrl: AlertController) {

}

presentAlert() {
  let alert = this.alertCtrl.create({
    title: 'Low battery',
    subTitle: '10% of battery remaining',
    buttons: ['Dismiss']
  });
  alert.present();
}

presentConfirm() {
  let alert = this.alertCtrl.create({
    title: 'Confirm purchase',
    message: 'Do you want to buy this book?',
    buttons: [
      {
        text: 'Cancel',
        role: 'cancel',
        handler: () => {
          console.log('Cancel clicked');
        }
      },
      {
        text: 'Buy',
        handler: () => {
          console.log('Buy clicked');
        }
      }
    ]
  });
  alert.present();
}

presentPrompt() {
  let alert = this.alertCtrl.create({
    title: 'Login',
    inputs: [
      {
        name: 'username',
        placeholder: 'Username'
      },
      {
        name: 'password',
        placeholder: 'Password',
        type: 'password'
      }
    ],
    buttons: [
      {
        text: 'Cancel',
        role: 'cancel',
        handler: data => {
          console.log('Cancel clicked');
        }
      },
      {
        text: 'Login',
        handler: data => {
          if (User.isValid(data.username, data.password)) {
            // logged in!
          } else {
            // invalid login
            return false;
          }
        }
      }
    ]
  });
  alert.present();
}
	</code>
</pre>

##实例成员
**config**
**create(opts)**
显示一个拥有题目，输入框和按钮的警示栏
<table>
	<tr>
		<th>参数</th>
		<th>类型</th>
		<th>描述</th>
	</tr>
	<tr>
		<td>opts</td>
		<td>AlertOptions</td>
		<td>参照下表</td>
	</tr>
</table>
##高级
Alert options
<table>
	<tr>
		<th>属性</th>
		<th>类型</th>
		<th>描述</th>
	</tr>
	<tr>
		<td>title</td>
		<td>string</td>
		<td>警示栏的标题</td>
	</tr>
	<tr>
		<td>subTitle</td>
		<td>string</td>
		<td>警示栏的副标题</td>
	</tr>
	<tr>
		<td>message</td>
		<td>string</td>
		<td>警示栏的内容</td>
	</tr>
	<tr>
		<td>cssClass</td>
		<td>string</td>
		<td>添加额外的css样式，以空格分隔</td>
	</tr>
	<tr>
		<td>inputs</td>
		<td>array</td>
		<td>一个警示栏里的输入栏数组，详见输入选项</td>
	</tr>
	<tr>
		<td>buttons</td>
		<td>array</td>
		<td>一个警示栏里的按钮数组，详见按钮选项</td>
	</tr>
	<tr>
		<td>enableBackdropDismiss</td>
		<td>boolean</td>
		<td>是否这个警示框可以被轻触背景关闭</td>
	</tr>
</table>
Input options
<table>
		<tr>
			<th>属性</th>
			<th>类型</th>
			<th>描述</th>
		</tr>
		<tr>
			<td>type</td>
			<td>string</td>
			<td>输入类型应该是：文本、电话、数字等等</td>
		</tr>
		<tr>
			<td>name</td>
			<td>string</td>
			<td>输入框的名称</td>
		</tr>
		<tr>
			<td>placeholder</td>
			<td>string</td>
			<td>这个输入框的容器（为了文字、数字输入框）</td>
		</tr>
		<tr>
			<td>value</td>
			<td>string</td>
			<td>这个输入框的值</td>
		</tr>
		<tr>
			<td>label</td>
			<td>string</td>
			<td>输入框的标签（只有多选/单选框可用）</td>
		</tr>
		<tr>
			<td>checked</td>
			<td>boolean</td>
			<td>输入框是否被选中</td>
		</tr>
		<tr>
			<td>id</td>
			<td>boolean</td>
			<td>这个输入框的id</td>
		</tr>
</table>
Button option
<table>
	<tr>
		<th>属性</th>
		<th>类型</th>
		<th>描述</th>
	</tr>
	<tr>
		<th>text</th>
		<th>string</th>
		<th>这个按钮展示的内容</th>
	</tr>
	<tr>
		<th>handler</th>
		<th>any</th>
		<th>当按钮被按下时触发</th>
	</tr>
	<tr>
		<th>cssClass</th>
		<th>string</th>
		<th>一个赋予这个按钮的额外的css属性</th>
	</tr>
	<tr>
		<th>role</th>
		<th>string</th>
		<th>按钮的role，null或者是cancel</th>
	</tr>
</table>
##取消和异步导航
在Alert被关闭以后，这个app可能需要依据handler的逻辑跳转到另一个页面。然而，因为多重跳转在同时被平等的对待，对于导航控制器来说很难做到干净利落的去异步渲染多重动画跳转。这一点在Nav Transition Promises部分中做了更详细的解释。对于Alert来说，这意味着在同一导航控制器中最好在开始一个新的跳转之前等待完成alert的跳转。  
在下方的例子中，在按钮被点击之后，它的handler等待异步操作来完成，然后它使用pop来导航回同一栈中的上一个页面。潜在的问题是异步操作可能已经在alert动画完成前完成。这种情况下，最好首先确认alert已经完成了过渡，然后再启动下一个过渡。
<pre>
	<code>let alert = this.alertCtrl.create({
  title: 'Hello',
  buttons: [{
    text: 'Ok',
    handler: () => {
      // user has clicked the alert button
      // begin the alert's dismiss transition
      let navTransition = alert.dismiss();

      // start some async method
      someAsyncOperation().then(() => {
        // once the async operation has completed
        // then run the next nav transition after the
        // first transition has finished animating out

        navTransition.then(() => {
          this.nav.pop();
        });
      });
      return false;
    }
  }]
});

alert.present();</code>
</pre>
标注出handler返回false很重要。一个按钮handlers特性是它们会自动关闭alert当它们的按钮被按下的时候，然而，我们需要更多的去控制跳转。因为handler返回了false，然后alert不自动关闭自己。相反的，你现在必须当alert结束过渡后的操控，以及在开始一个新跳转之前等待alert完成过渡。


[sass变量](http://ionicframework.com/docs/api/components/alert/AlertController/#sass-variables)
