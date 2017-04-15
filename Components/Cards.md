### Cards
Cards(卡片)是展示页面中一片重要区域的很好的方式，这样的展现方式正成为app设计中核心的设计模式。它是一种非常好的展示和组织信息的方式，同时对于用户来说也不会觉得突兀。由于经常需要在手机较小的屏幕上展示大量的信息，Cards迅速成为了许多公司的绝佳选择，包括谷歌，推特，和Spotify公司。

对于移动体验而言，Cards使得在众多屏幕尺寸上以相似的视觉效果呈现信息更加容易。它们可被控制，富有弹性，甚至有动画效果。Cards常被放置在其他组件之上，但它们也可以当做“page”使用，可以通过左右滑动来切换。

`其他内容`
[Basic Cards](http://ionicframework.com/docs/components/#cards)

[Card Headers](http://ionicframework.com/docs/components/#card-header)

[Card Lists](http://ionicframework.com/docs/components/#card-list)

[Card Images](http://ionicframework.com/docs/components/#card-image)

[Background Images](http://ionicframework.com/docs/components/#card-background)

[Advanced Cards](http://ionicframework.com/docs/components/#advanced-cards)


#### 基本使用 ####
Cards是一个基本的css组件。按照下面的方式来使用基本的cards:
```
<ion-card>

  <ion-card-header>
    Card Header
  </ion-card-header>

  <ion-card-content>
    <!-- Add card content here! -->
  </ion-card-content>

</ion-card>
```

### Card Headers
就像一个普通的页面一样，cards也可以自定义的包含头部，要在cards中添加头部，只需在cards中添加`<ion-card-header>`组件：
```
<ion-card>
  <ion-card-header>
    Header
  </ion-card-header>
  <ion-card-content>
    The British use the term "header", but the American term "head-shot" the English simply refuse to adopt.
  </ion-card-content>
</ion-card>
```

### Lists In Cards

一个card可以包含一个列表，在card的`<ion-card-content>`中加入`ion-list`即可：
```
<ion-card>
  <ion-card-header>
    Explore Nearby
  </ion-card-header>

  <ion-list>
    <button ion-item>
      <ion-icon name="cart" item-left></ion-icon>
      Shopping
    </button>

    <button ion-item>
      <ion-icon name="medical" item-left></ion-icon>
      Hospital
    </button>

    <button ion-item>
      <ion-icon name="cafe" item-left></ion-icon>
      Cafe
    </button>

    <button ion-item>
      <ion-icon name="paw" item-left></ion-icon>
      Dog Park
    </button>

    <button ion-item>
      <ion-icon name="beer" item-left></ion-icon>
      Pub
    </button>

    <button ion-item>
      <ion-icon name="planet" item-left></ion-icon>
      Space
    </button>

  </ion-list>
</ion-card>
```

### Images In Cards
图片常常有不同的尺寸，所以在你的app中给它们设置一致的样式是很重要的。在card中加入图片很容易。card中的图片将拥有固定的宽高。列表、头部、以及其他的card组件都可以很方便的和图片结合在一起。要在card中添加图片，按照下面的方式：
```
<ion-card>
  <img src="img/nin-live.png"/>
  <ion-card-content>
    <ion-card-title>
      Nine Inch Nails Live
      </ion-card-title>
    <p>
      The most popular industrial group ever, and largely
      responsible for bringing the music to a mass audience.
    </p>
  </ion-card-content>
</ion-card>
```

### Background Images
Card可以实现多种设计。我们提供许多元素来实现（体验）一致的设计，但有时候也要添加一些自定义样式。为card设置背景图片就是个很好的例子：

下面的html代码可被添加到页面的内容部分：

```
<ion-content class="card-background-page">

  <ion-card>
    <img src="img/card-saopaolo.png"/>
    <div class="card-title">São Paulo</div>
    <div class="card-subtitle">41 Listings</div>
  </ion-card>

  <ion-card>
    <img src="img/card-amsterdam.png"/>
    <div class="card-title">Amsterdam</div>
    <div class="card-subtitle">64 Listings</div>
  </ion-card>

  <ion-card>
    <img src="img/card-sf.png"/>
    <div class="card-title">San Francisco</div>
    <div class="card-subtitle">72 Listings</div>
  </ion-card>

  <ion-card>
    <img src="img/card-madison.png"/>
    <div class="card-title">Madison</div>
    <div class="card-subtitle">28 Listings</div>
  </ion-card>

</ion-content>
```

然后在页面的sass文件中：
```
.card-background-page {

  ion-card {
    position: relative;
    text-align: center;
  }

  .card-title {
    position: absolute;
    top: 36%;
    font-size: 2.0em;
    width: 100%;
    font-weight: bold;
    color: #fff;
  }

  .card-subtitle {
    font-size: 1.0em;
    position: absolute;
    top: 52%;
    width: 100%;
    color: #fff;
  }

}
```

### Advanced Cards
不同类型的card样式可以组合出高级的cards。cards也可以用自己的css样式。下面的几个高级cards是用自定义css样式构建的：

`Contents`
[Social Cards](http://ionicframework.com/docs/components/#card-advanced-social)
[Map Cards](http://ionicframework.com/docs/components/#card-advanced-map)

### Social Cards
在app中经常需要创建社会化的卡片，在cards中使用不同的组件可以实现这样的需求：

```
<ion-card>

  <ion-item>
    <ion-avatar item-left>
      <img src="img/marty-avatar.png">
    </ion-avatar>
    <h2>Marty McFly</h2>
    <p>November 5, 1955</p>
  </ion-item>

  <img src="img/advance-card-bttf.png">

  <ion-card-content>
    <p>Wait a minute. Wait a minute, Doc. Uhhh... Are you telling me that you built a time machine... out of a DeLorean?! Whoa. This is heavy.</p>
  </ion-card-content>

  <ion-row>
    <ion-col>
      <button ion-button icon-left clear small>
        <ion-icon name="thumbs-up"></ion-icon>
        <div>12 Likes</div>
      </button>
    </ion-col>
    <ion-col>
      <button ion-button icon-left clear small>
        <ion-icon name="text"></ion-icon>
        <div>4 Comments</div>
      </button>
    </ion-col>
    <ion-col center text-center>
      <ion-note>
        11h ago
      </ion-note>
    </ion-col>
  </ion-row>

</ion-card>
```

### Map Cards
ionic中不同的组件组合起来可以创建类似地图的组件：
```

<ion-card>

  <img src="img/advance-card-map-madison.png">
  <ion-fab right top>
    <button ion-fab>
      <ion-icon name="pin"></ion-icon>
    </button>
  </ion-fab>

  <ion-item>
    <ion-icon name="football" item-left large></ion-icon>
    <h2>Museum of Football</h2>
    <p>11 N. Way St, Madison, WI 53703</p>
  </ion-item>

  <ion-item>
    <ion-icon name="wine" item-left large ></ion-icon>
    <h2>Institute of Fine Cocktails</h2>
    <p>14 S. Hop Avenue, Madison, WI 53703</p>
  </ion-item>

  <ion-item>
    <span item-left>18 min</span>
    <span item-left>(2.6 mi)</span>
    <button ion-button icon-left clear item-right>
      <ion-icon name="navigate"></ion-icon>
      Start
    </button>
  </ion-item>

</ion-card>

```