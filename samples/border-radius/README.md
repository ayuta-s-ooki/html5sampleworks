#Border radius

border-radiusを使うと、画像を使わずに角丸を表示することが可能です。

##対応状況

[CSS3 Border-radius](http://caniuse.com/#feat=border-radius)

##プロパティ

四隅をそれぞれ指定する方法と、一括でまとめて指定する方法があります。

特定の部分だけを角丸指定する場合は、角丸にしたい場所にそれぞれ対応しているプロパティを指定します。

```
border-top-left-radius, border-top-right-radius, border-bottom-right-radius, border-bottom-left-radius
```

一括でまとめて指定する場合は、下記のプロパティを使用します。

```
border-radius
```

また、それぞれにベンダープレフィックスが必要となります。

##サンプル
サンプルは、ボックスを3つ用意して、それぞれ角丸指定なし、一括でまとめて角丸指定したもの、左上のみ角丸指定しています。

```
<div id="box1" class="box">none;</div>
<div id="box2" class="box">border-radius: 25px;</div>
<div id="box3" class="box">border-top-left-radius: 50px;</div>
```


##サンプルコード
##参考

- [Specification](http://www.w3.org/TR/css3-background/#the-border-radius)
- [CSS Border Radius Generator](http://border-radius.com/)
