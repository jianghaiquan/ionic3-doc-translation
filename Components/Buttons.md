
### Buttons
Buttons�ǹᴩ����app�е���Ҫ�Ľ�����ʽ�����û����ʱӦ������ȷ�Ľ�����Buttons��������ͼ������֣��ҿ���ͨ���ǳ������������ǿ��

����˵��Buttons���ñ�׼��<button>��ǩ��ʵ�֣�������ʵ�Ѿ���ion-buttonָ������˼�ǿ��

������Ϣ��鿴API�ĵ���

����ʹ�ã�
```
<button ion-button>Button</button>
```
color���Կ�������button����ɫ��ionic���ö���Ĭ����ɫ���ҿ��Ժ����׵ĸ�д��
```
<button ion-button color="light">Light</button>
<button ion-button>Default</button>
<button ion-button color="secondary">Secondary</button>
<button ion-button color="danger">Danger</button>
<button ion-button color="dark">Dark</button>
```
### Outline Style
Ҫʹ��Outline����Button���������Outline���ԣ�
```
<button ion-button color="light" outline>Light Outline</button>
<button ion-button outline>Primary Outline</button>
<button ion-button color="secondary" outline>Secondary Outline</button>
<button ion-button color="danger" outline>Danger Outline</button>
<button ion-button color="dark" outline>Dark Outline</button>
```
### Clear Style
Ҫʹ��Clear����Button���������Clear���ԣ�
```
<button ion-button color="light" clear>Light Clear</button>
<button ion-button clear>Primary Clear</button>
<button ion-button color="secondary" clear>Secondary Clear</button>
<button ion-button color="danger" clear>Danger Clear</button>
<button ion-button color="dark" clear>Dark Clear</button>
```
### Round Buttons
Ҫ����Բ�ǰ�ť��ֻ�����round���ԣ�
```
<button ion-button color="light" round>Light Round</button>
<button ion-button round>Primary Round</button>
<button ion-button color="secondary" round>Secondary Round</button>
<button ion-button color="danger" round>Danger Round</button>
<button ion-button color="dark" round>Dark Round</button>
```
### Block Buttons
���block���Ի�ʹ��ť��Ⱥ��丸Ԫ����ȣ��������display:block���Ե���ť�ϣ�
```
<button ion-button block>Block Button</button>
```
### Full Buttons
���full���Ե�һ����ť�ϣ���ʹ��ť�ﵽ100%�丸Ԫ�صĿ�ȡ�Ȼ��Ҳ���Ƴ���ť�����ұ߿򡣵�һ����ť��Ҫ���������ȵ�ʱ�򣬿�����������ԡ�
```
<button ion-button full>Full Button</button>
```
### Button Sizes
���large���Կ�����һ����ť��ø��󣬻������small����ʹ��ť��ø�С��
```
<button ion-button small>Small</button>
<button ion-button>Default</button>
<button ion-button large>Large</button>
```
### Icon Buttons
Ϊһ����ť���ͼ�꣬�����ڰ�ť��ʹ��icon���������������position���ԣ�
```
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
```
### Buttons In Components
���ܰ�ť���Ե���ʹ�ã���Ҳ���Ժ����׵������������ʹ�ã����磬��ť�������б���б�����ʹ�ã������ڵ�������ʹ�ã�
```
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
```