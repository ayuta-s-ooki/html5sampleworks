#CSS Content

`content`と呼ばれるCSSプロパティは、要素の直前または直後に、文字列や画像などのコンテンツを挿入する際に使用します。それぞれ`:after`や`:before`セレクタ疑似要素を使って指定します。

##対応状況

[CSS Generated content](http://caniuse.com/#feat=css-gencontent)

##プロパティ

contentの指定方法は、下記のようになります。

```
#contents:before {
  content: '値'	// テキスト OR 画像 OR その他[css counter()など]
}
```


##サンプル
サンプルでは、リスト要素の直前にラベルを挿入しています。

##参考

- [Specification](http://www.w3.org/TR/CSS21/generate.html)
- [Specification日本語](http://momdo.s35.xrea.com/web-html-test/spec/CSS21/generate.html)
