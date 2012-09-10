#FullScreen API
##API

```
partial interface Element {
  requestFullscreen: {Function}     // 要素をフルスクリーンで表示する
}

partial interface Document {
  fullscreenEnabled: {boolean},     // フルスクリーンAPI対応している場合true
  fullscreenElement: {?Element},    // フルスクリーン表示されている要素を返す
  exitFullscreen: {Function}        // フルスクリーン表示を停止する
}
```

これらのAPIには、ベンダープレフィックスが必要です。

Webkit系ブラウザであれば、`requestFullscreen`は`webkitRequestFullscreen`となります。

##サンプル
ビデオ要素とフルスクリーン用ボタン要素を含む領域をフルスクリーンにするサンプルになります。

##サンプルコード

ベンダープレフィックスを指定するのが面倒なので、[Modernizer]()の`prefix`メソッドを使用しています。*フルスクリーンで見る*ボタンをクリックすると、フルスクリーンになり、*フルスクリーンを解除*ボタンをクリックすると、通常の画面に戻ります。

**フルスクリーン対象のHTML

```
<div id="container">
<!-- Video source: http://www.w3.org/2010/05/video/mediaevents.html -->
<video id="video" controls>
<source id="mp4" src="http://media.w3.org/2010/05/sintel/trailer.mp4" type="video/mp4">
<source id="webm" src="http://media.w3.org/2010/05/sintel/trailer.webm" type="video/webm">
<source id="ogv" src="http://media.w3.org/2010/05/sintel/trailer.ogv" type="video/ogg">
<p>このブラウザは、HTML5 Video 要素に対応していません。</p>
</video>
<div id="controller">
<button id="enterBtn">フルスクリーンで見る</button>
<button id="exitBtn">フルスクリーンを解除</button>
</div>
</div>
```

そして、ボタンのクリックイベントにより、フルスクリーン表示/非表示を切り替えます。

```
(function(global) {
  var enterBtn = document.getElementById('enterBtn'),
      exitBtn = document.getElementById('exitBtn'),
      container = document.getElementById('container');

  // フルスクリーンきりかえ
  function enterFullScreen() {
    var fn = Modernizr.prefixed('requestFullscreen', container);
    if (!fn) {  // 旧APIを試す
      fn = Modernizr.prefixed('requestFullScreen', container);
    }
    fn && fn();
  }

  // フルスクリーン解除
  function exitFullScreen() {
    var fn = Modernizr.prefixed('exitFullscreen', document);
    if (!fn) {  // 旧APIを試す
      fn = Modernizr.prefixed('cancelFullScreen', document);
    }
    fn && fn();
  }

  enterBtn.addEventListener('click', enterFullScreen, false);
  exitBtn.addEventListener('click', exitFullScreen, false);
}(this));
```

##参考

[Fullscreen](http://dvcs.w3.org/hg/fullscreen/raw-file/tip/Overview.html)
