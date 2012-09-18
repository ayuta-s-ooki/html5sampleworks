#Audio element/Audio API

Audio要素を使うとブラウザで音声を再生することが可能です。また、Javascriptでコンストラクタを使って生成し、APIにアクセスして制御することも可能になっています。

##対応状況

[audio element](http://caniuse.com/#feat=audio)

##API

###Audio要素の属性

下記の5つの属性が定義されています。これらは、`<video>`要素と共通です。

- `src` - コンテンツソースのURL
- `preload` - ブラウザへの事前バッファリング制御通知(この属性に従うかはブラウザー依存)
	- `none` - バッファリングは必要ない
	- `metadata` - メタデータのみ
	- **`auto`** - 前もってメディアリソースをダウンロードしてもよい(デフォルト)
- `autoplay` - ファイルを自動再生するかどうか
- `mediagroup` - 複数のメディア要素(`<audio>` | `<video>`)を連結し同期再生するためのグループ化属性
- `loop` - 繰り返し再生するかどうか
- `controls` - ブラウザー組み込みのコントローラーを使用するかどうか

また、`<audio>`要素の`src`属性を使わず、`<source>`要素を使うことでクロスブラウザ対応で、複数のフォーマットを指定することが可能です。

***例***

```
<audio controls preload="auto">
  <source src="audio.ogg" />
  <source src="audio.mp3" />
</audio>
```

###Audioコンストラクタ

`<audio>`は、`<img>`の`Image`コンストラクタと同じく、`Audio`というコンストラクタが存在するため、
組み込みのコントローラーを必要とせずJavascriptで制御したい場合、ページのDOMツリーに要素を追加しないで、
音声を再生する場合に使用することが可能です。
`document.createElement('audio')`を使用する場合と異なり、デフォルト属性も同時にセットされます。

***Audioコンストラクタ***

```
var audio = new Audio();		// 空の<audio>を生成する
var audio2 = new Audio(url);	// 音声データURLを引数に<audio>を生成。`src`属性をセットするのと同等
```

###Audio API

`<audio>`要素の組み込みコントローラーを使うのでなければ、音声のコントロールは、Javascriptを用いて行います。音声のバッファリング状態や再生状態などが、Audio APIを使って状態チェックを行う必要があります。たくさんありますので、ここでは一部のみ紹介します。

- `currentTime` - 現在の再生位置を表す秒数
- `duration` - メディアリソースの長さを表す秒数
- `paused` - 一時停止中かどうか
- `enbed` - 再生終了しているかどうか
- `load()` - 読み込みし直す
- `pause()` - 再生を一時停止する
- `play()` - 現在の再生位置から再生を開始する

###イベント

`<audio>`要素は、読み込みや再生中にさまざまなイベントを発生させます。これらのイベントをJavascriptで補足して処理を行います。これもたくさんありますので、一部のみ紹介します。

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
サンプルでは、`<audio>`タグと`<source>`タグを使い、複数のオーディオフォーマットのファイルを指定し、様々なブラウザーで再生できるようにしています。`preload`属性がデフォルトで`auto`なので、オーディオデータの読み込みが開始され、`canplaythrough`で再生可能になったら、`play()`で再生しています。また、各イベントが発生したタイミングを画面に出力しているのを確認してみてください。

```
  <audio id="defaultController" controls loop>
    <source src="http://media.w3.org/2010/07/bunny/04-Death_Becomes_Fur.oga"/>
    <source src="http://media.w3.org/2010/07/bunny/04-Death_Becomes_Fur.wav"/>
    <source src="http://media.w3.org/2010/07/bunny/04-Death_Becomes_Fur.mp3"/>
    <source src="http://media.w3.org/2010/07/bunny/04-Death_Becomes_Fur.mp4"/>
  </audio>
```

[Audio elementサンプル](http://ayuta-s-ooki.github.com/html5sampleworks/samples/audio/)

##サンプルコード

- [download](http://ayuta-s-ooki.github.com/html5sampleworks/downloads/audio.zip)

##参考

- [Specification](http://www.whatwg.org/specs/web-apps/current-work/multipage/the-video-element.html#audio)
- [Reference](http://www.w3.org/wiki/HTML/Elements/audio)
