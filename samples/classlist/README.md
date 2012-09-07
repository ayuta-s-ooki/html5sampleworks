#classList

classListは、DOM要素のclass属性トークンリストを返し、そのトークンリストを使って、クラス属性の追加/削除/toggleなどの操作が可能です。
jQueryなどのライブラリを使って実現していたことが、ネイティブに処理することが可能になります。

##対応状況

- [classList](http://caniuse.com/#search=classlist)

##API

classListは、要素のプロパティとして定義されています。

```
interface Element {
    classList: {DOMTokenList}
}
```

そして、その中にクラス属性を操作するAPIが用意されています。

```
// classListプロパティの中身
interface DOMTokenList {
  length: {number},                         // 要素のクラス属性数
  add: {function(string)},                  // クラス属性追加
  contains: {function(string): boolean},    // クラス属性の存在チェック
  item: {function(number): string},         // クラス属性をインデックスで取得
  remove: {function(string)},               // 要素からクラス属性を削除
  toggle: {function(string)}                // クラス属性追加/削除トグルスイッチ
}
```

##サンプル

classListのAPIを使って、DOM要素にクラス属性追加/削除を行います。クラスに紐づけられたスタイル適用されます。
追加、削除、トグルAPIでスタイルの適用を行います。

##参考

- [classList](https://developer.mozilla.org/ja/docs/DOM/element.classList)
