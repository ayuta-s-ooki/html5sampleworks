#getComputedStyle

要素に対して適用される全ての CSS プロパティにおいて最終的に算出されたスタイルを返します。ある要素の`style`属性に直接記述されているものではなく、CSSのスタイルを適用した要素のスタイルを取得するための用途に使ったりするものです。

##対応状況

[getComputedStyle](http://caniuse.com/#feat=getcomputedstyle)

##構文

`getComputedStyle`は、2つの引数をとります。

```
var style = document.getComputedStyle(element, pseudoElt);
```

- `element`: `document.getElementById`等で取得できる要素オブジェクトです。
- `pseudoElt`: 疑似要素です。下記のものがあります。`:hover`などは疑似クラスと呼ばれるものなので異なります。
	- `:first-letter`
	- `:first-line`
	- `:before`
	- `:last`

***例***

```
var text = document.getElementById(“text”);
var textStyles = document.defaultView.getComputedStyle(text, ':first-letter');
```

##サンプル
このサンプルでは、`<p>`要素と`<div>`要素に適用されたスタイルを取得して、画面上に出力しています。比較のためにCSSも出力しています。

```
<div id="container">
  <div id="content" class="col">
    <p id="text">テストサンプル</p>
    <div id="box1" class="box">box1</div>
  </div>
  <div id="baseStyle" class="col printer"></div>
  <div id="debug" class="col printer"></div>
  <div id="clearfix"></div>
</div>
```

[getComputedStyleサンプル](http://ayuta-s-ooki.github.com/html5sampleworks/samples/getcomputedstyle/)

##サンプルコード

- [download](http://ayuta-s-ooki.github.com/html5sampleworks/downloads/getcomputedstyle.zip)


`getComputedStyle`を使い、対象の要素のスタイルを取得し画面上に出力しています。

```
    // textの算出済みスタイルを取得
    var textStyles = document.defaultView.getComputedStyle(text, ':first-letter');
    // boxの算出済みスタイルを取得
    var boxStyles = document.defaultView.getComputedStyle(box);

    // 算出済みスタイルはキャメルケースで取得できる(font-size -> fontSize)
    buf = [];
    buf[buf.length] = createParagraph('Computed Style');
    buf[buf.length] = createParagraph('p:first-letter {');
    buf[buf.length] = createParagraph('  font-size: ' + textStyles.fontSize);
    buf[buf.length] = createParagraph('  background-color: ' + textStyles.backgroundColor);
    buf[buf.length] = createParagraph('  color: ' + textStyles.color);
    buf[buf.length] = createParagraph('}');
    buf[buf.length] = createParagraph('.box {');
    buf[buf.length] = createParagraph('  width: ' + boxStyles.width);
    buf[buf.length] = createParagraph('  height: ' + boxStyles.height);
    buf[buf.length] = createParagraph('  margin: ' + boxStyles.margin);
    buf[buf.length] = createParagraph('  background-color: ' + boxStyles.backgroundColor);
    buf[buf.length] = createParagraph('  color: ' + boxStyles.color);
    buf[buf.length] = createParagraph('}');

    // 算出済みスタイルを画面に出力
    debug.innerHTML = buf.join('');
```


##参考

- [Specification](http://www.w3.org/TR/DOM-Level-2-Style/css.html#CSS-CSSview-getComputedStyle)
