# 排版 #

 `[ion-text]`

排版组件是一个简单的组件，它可以用来设置文本任何元素文本的颜色。为了从 `$colors` map 传递一个颜色值来改变元素文本的颜色，应该为那个元素添加 `ion-text` 属性。

### 用法 ###

    <h1 ion-text color="secondary">H1: The quick brown fox jumps over the lazy dog</h1>
    
    <h2 ion-text color="primary">H2: The quick brown fox jumps over the lazy dog</h2>
    
    <h3 ion-text color="light">H3: The quick brown fox jumps over the lazy dog</h3>
    
    <h4 ion-text color="danger">H4: The quick brown fox jumps over the lazy dog</h4>
    
    <h5 ion-text color="dark">H5: The quick brown fox jumps over the lazy dog</h5>
    
    <h6 ion-text [color]="dynamicColor">H6: The quick brown fox jumps over the lazy dog</h6>
    
    <p>
      I saw a werewolf with a Chinese menu in his hand.
      Walking through the <sub ion-text color="danger">streets</sub> of Soho in the rain.
      He <i ion-text color="primary">was</i> looking for a place called Lee Ho Fook's.
      Gonna get a <a ion-text color="secondary">big dish of beef chow mein.</a>
    </p>
    
    <p>
      He's the hairy-handed gent who ran amuck in Kent.
      Lately he's <sup ion-text color="primary">been</sup> overheard in Mayfair.
      Better stay away from him.
      He'll rip your lungs out, Jim.
      I'd like to meet his tailor.
    </p>