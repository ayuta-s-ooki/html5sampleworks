#matchMedia

`matchMedia`を使用すると、メディアクエリの結果を確認し、結果が変化した時に通知を受け取ることが可能となります。
メディアクエリとは、CSSで使われているメディアタイプとメディア特性のセットのことです。CSS3になりさらに強化されました。

印刷プレビュー用に別のスタイルを割り当てる等で使用したりする機能です。最近では、レスポンシブWebデザインで使われることが多くなってきました。

***HTMLの例***

```
<link rel="stylesheet" media="screen" href="example.css" />
```

***CSSの例***

```
/* メディアタイプ and (メディア特性) */
@media print and (min-resolution: 300dpi) { ... }
```

このメディアクエリをJavascriptで扱うことを可能にしたのが、`matchMedia`です。

##対応状況

[matchMedia](http://caniuse.com/#feat=matchmedia)

##API

`matchMedia`を使ってできることは下記の通りです。1つ目で作成したメディアクエリリストのメソッドやプロパティが用意されているので、それを使います。

- `window.matchMedia()` - メディアクエリリストを作成
- `mediaQueryList.matches` - クエリ結果を確認
- `mediaQueryList.media` - シリアライズされたメディアクエリのリストを取得
- `mediaQueryList.addListener()` - クエリ通知を受け取るリスナーを追加
- `mediaQueryList.removeListener()` - クエリ通知のリスナーを削除する

###メディアクエリリストの作成

```
var widthQuery = window.matchMedia("(min-width: 600px)");  // viewportの幅が600px以上か調べるクエリリスト
var portraitQuery = window.matchMedia("(orientation: portrait)");  // デバイスが横か縦か調べるクエリリスト
```

##サンプル
幅とデバイスの向きに関するクエリの動作を確かめられます。ウィンドウをサイズ変更して値がどのように変わるか確認してみてください。

[matchMediaサンプル](http://ayuta-s-ooki.github.com/html5sampleworks/matchmedia/)

##サンプルコード

- [downloads](http://ayuta-s-ooki.github.com/html5sampleworks/downloads/matchmedia.zip)

##参考

- [Specification](http://www.w3.org/TR/cssom-view/#dom-window-matchmedia)
