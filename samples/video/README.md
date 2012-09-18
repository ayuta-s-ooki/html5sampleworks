#Video element/Video API

Video要素を使うとブラウザで動画再生することが可能です。また、JavascriptでAPIにアクセスして制御することも可能になっています。

##対応状況

[Video element](http://caniuse.com/#feat=video)

##API

###Video要素の属性

下記の属性が定義されています。これらは、`<audio>`要素と共通です。

- `src` - コンテンツソースのURL
- `preload` - ブラウザへの事前バッファリング制御通知(この属性に従うかはブラウザー依存)
	- `none` - バッファリングは必要ない
	- `metadata` - メタデータのみ
	- **`auto`** - 前もってメディアリソースをダウンロードしてもよい(デフォルト)
- `autoplay` - ファイルを自動再生するかどうか
- `mediagroup` - 複数のメディア要素(`<audio>` | `<video>`)を連結し同期再生するためのグループ化属性
- `loop` - 繰り返し再生するかどうか
- `muted` - 消音しているかどうか
- `controls` - ブラウザー組み込みのコントローラーを使用するかどうか

`<video>`要素独自の属性もあります。

- `width` - 動画の幅
- `height` - 動画の高さ
- `poster` - 動画データを利用できない場合に代わりに表示する画像

また、`<video>`要素の`src`属性を使わず、`<source>`要素を使うことでクロスブラウザ対応で、複数のフォーマットを指定することが可能です。

***例***

```
<video controls preload="auto">
  <source id="mp4" src="http://media.w3.org/2010/05/sintel/trailer.mp4" type="video/mp4">
  <source id="webm" src="http://media.w3.org/2010/05/sintel/trailer.webm" type="video/webm">
  <source id="ogv" src="http://media.w3.org/2010/05/sintel/trailer.ogv" type="video/ogg">
</video>
```

###Video API

動画のバッファリング状態や再生状態などが、Video APIを使って状態チェックを行う必要があります。たくさんありますので、ここでは一部のみ紹介します。

- `currentTime` - 現在の再生位置を表す秒数
- `duration` - メディアリソースの長さを表す秒数
- `paused` - 一時停止中かどうか
- `enbed` - 再生終了しているかどうか
- `load()` - 読み込みし直す
- `pause()` - 再生を一時停止する
- `play()` - 現在の再生位置から再生を開始する

###イベント

`<video>`要素は、読み込みや再生中にさまざまなイベントを発生させます。これらのイベントをJavascriptで補足して処理を行います。これもたくさんありますので、一部のみ紹介します。

- `loadstart` - データ読み込み開始
- `progress` - データ読み込み中(ダウンロードが続いているのであれば何度も)
- `loadmetadata` - メタデータを読み込んだ
- `canplay` - 再生開始できる程度にデータを読み込んだ
- `canplaythrough` - このままのダウンロード速度が続けば、最後まで再生できる程度にデータを読み込んだ
- `load` - メディアリソースのダウンロードが完了した
- `abort` - ダウンロードがエラーにより中止された
- `error` - エラーが発生した
- `loadend` - データの読み込みが完了(`load` | `abort` | `error`　後に発生)
- `playing` - 再生が開始された
- `waiting` - 次のフレームダウンロード待ち
- `ended` - 再生終了

##サンプル
サンプルでは、`<video>`タグと`<source>`タグを使い、複数のオーディオフォーマットのファイルを指定し、様々なブラウザーで再生できるようにしています。`preload`属性がデフォルトで`auto`なので、オーディオデータの読み込みが開始され、`canplaythrough`で再生可能になったら、`play()`で再生しています。また、各イベントが発生したタイミングを画面に出力しているのを確認してみてください。

```
<video id="defaultController" width="450" height="300" controls loop poster="http://www.w3.org/wiki/images/0/07/Video02.png">
  <!-- Video source: http://www.w3.org/2010/05/video/mediaevents.html -->
  <source id="mp4" src="http://media.w3.org/2010/05/sintel/trailer.mp4" type="video/mp4">
  <source id="webm" src="http://media.w3.org/2010/05/sintel/trailer.webm" type="video/webm">
  <source id="ogv" src="http://media.w3.org/2010/05/sintel/trailer.ogv" type="video/ogg">
  <p>このブラウザは、HTML5 Video 要素に対応していません。</p>
</video>
```

[Video elementサンプル](http://ayuta-s-ooki.github.com/html5sampleworks/samples/video/)

##サンプルコード

- [download](http://ayuta-s-ooki.github.com/html5sampleworks/downloads/video.zip)

##参考

- [Specification](http://www.whatwg.org/specs/web-apps/current-work/multipage/the-video-element.html#video)
- [Reference](http://www.w3.org/wiki/HTML/Elements/video)
