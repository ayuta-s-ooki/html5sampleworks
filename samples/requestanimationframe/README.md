#RequestAnimationFrame

`setTimeout`や`setInterval`を使ったアニメーションは過剰に描画されることが多く、CPU サイクルを浪費し電力消費を増やす原因となります。Webサイトが表示されていないとき、特に Webサイトがバックグラウンド タブのページで開かれているときやブラウザーが最小化されているときにも、アニメーションが頻繁に再生されます。また、アニメーションと表示更新のタイミングが合っていない場合に、画像が途切れることがあります。
`requestAnimationFrame`では、ブラウザーでページ表示の更新が必要なタイミングでのみ動作するため、適切な量のリソースだけが使われます。

##対応状況

[requestAnimationFrame](http://caniuse.com/#feat=requestanimationframe)

##API

アニメーション処理の開始と停止のメソッドがあります。`requestAnimationFrame`の引数の`callback`には、次に実行したい関数をわたします。`cancelAnimationFrame`の引数`handle`には、`requestAnimationFrame`の返り値を渡してキャンセル処理を行います。
`setTimeout`を使った繰り返し処理のような使い方になるでしょう。

```
interface WindowAnimationTiming {
  long requestAnimationFrame(FrameRequestCallback callback);  // アニメーション処理開始
  void cancelAnimationFrame(long handle);  // アニメーション処理キャンセル
};
```

##サンプル
このサンプルでは、`requestAnimationFrame`を使った図形移動アニメーションを実装しています。水色エリアをクリックしてアニメーション処理の開始と停止を行います。
##サンプルコード

- [download](http://ayuta-s-ooki.github.com/html5sampleworks/samples/requestanimationframe/)

##参考

- [Specification](http://www.w3.org/TR/animation-timing/#requestAnimationFrame)
