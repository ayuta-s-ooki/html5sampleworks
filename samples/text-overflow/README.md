#text-overflow
テキストが表示領域をオーバーフローしたときに、省略記号を表示するかどうかを指定できます。

##対応状況

[CSS3 Text-overflow](http://caniuse.com/#feat=text-overflow)

##プロパティ

```
text-overflow: ellipsis | clip | <custom>
```

- `ellipsis` 切り取られたテキストの代わりに、省略記号(…)を表示します。
- `clip` デフォルトの値です。テキストを切り取ります。
- `<custom>` 任意の2文字までの省略文字を指定できます。

また、`text-overflow` で省略記号表示するには、いくつかの追加プロパティを指定する必要があります。

例:

```
p {
  width: 100%;               /* IE6ではwidthの指定が必要 */
  overflow: hidden;          /* "visible"以外の値が必要 */
  text-overflow: ellipsis;
}
```

##サンプル
長い文章が、`text-overflow`の値によって切り取りの挙動が変わることが確認できます。最後のカスタム文字"-"は、Firefoxで確認することができます。(ChromeやSafariでは確認できません。)

##サンプルコード

- [download](http://ayuta-s-ooki.github.com/html5sampleworks/downloads/text-overflow.zip)

##参考

- [Specification](http://www.w3.org/TR/css3-ui/#text-overflow0)
