#Flexible Box Layout Module

CSSでレイアウトを行うために策定されている仕様の一つです。
UI設計用に最適化されたボックスモデルを提供します。

1. これまで難しかったレイアウト(nカラムレイアウト)を実現しやすい。
2. 非常に柔軟なレイアウトを作成可能で、高さなどは、ブラウザが勝手に計算して調整してくれます。

##指定方法

親ボックス要素で下記を指定

`display: box`

しかし、2012/09/06現在ではベンダープレフィックスが必要(IEはIE10から)

- Webkit系: `display: -webkit-box`
- Firefox: `display: -moz-box`
- IE: `display: -ms-box`

##Properties

###親ボックスに指定

- box-orient: ボックスの子の配置方法を指定
    - **horizontal**
    - vertical
    - inherit
- box-pack: `box-orient`の軸に沿ったボックスの配置を指定
    - **start**
    - end
    - center
    - justify
- box-align: `box-pack`と似たようなプロパティ。ボックスの整列を指定
    - start
    - end
    - center
    - baseline
    - **stretch**

###子ボックスに指定

- box-flex: ブラウザのサイズによって、フレキシブルに伸縮してくれる。0はflexibleなし。
    - **0**
    - 任意の整数
- box-flex-group
- box-ordinal-group: `display: box`内の子ボックスの表示順番を制御
- box-direction
- box-lines

##参考

- [CSS Flexible Box Layout Module](http://dev.w3.org/csswg/css3-flexbox/);
- [フレキシブル ボックス モデルを使ってみる](http://www.html5rocks.com/ja/tutorials/flexbox/quick/)
