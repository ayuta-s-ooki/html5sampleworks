#datalist

`<datalist>`は、ユーザーに入力候補の選択肢を提供するための要素です。選択肢の候補は、`<option>`要素が使われます。
この要素は子要素も含めて非表示になっており、input要素のサジェストなどに使用します。

##使い方

下記のように、datalistの`id`を、`<input>`の`list`属性に指定するとdatalistを使用することが可能になります。

```
<form action="javascript: void(0);" method="post">
<label for="title">投稿タイトル: </label><input type="search" id="title" size="120" list="posts">

<!-- データリストのリストを作成 -->
<datalist id="posts">
<option id="31264300234" value="花火をぶつけて、エイリアン"></option>
<!-- […] -->
</datalist>
</form>
```



##対応状況

[datalist](http://caniuse.com/#feat=datalist)

##サンプル
このサンプルでは、本ブログの最新投稿記事のリストをJSONPで取得して、その記事タイトルをdatalistの候補としてセットします。そして、検索バーの所にフォーカスを当てて、クリックすると選択肢の候補一覧がサジェスト機能のように表示されます。

```
<form action="javascript: void(0);" method="post">
<label for="title">投稿タイトル: </label><input type="search" id="title" size="120" list="posts">

<!-- データリストのリストを作成 -->
<datalist id="posts">
<option id="31264300234" value="花火をぶつけて、エイリアンを倒せ！iPhone,iPadアプリ「エイリアンVS花火職人」をリリースしました！(無料)"></option>
<option id="31263683351" value="vs"></option>
<option id="31263620741" value="vs"></option>
<option id="30857703525" value="「あゆたジャーナル」はじめました。"></option>
<option id="30857477426" value="Adobe Edge Animate入門"></option>
<option id="30857279965" value="[Adobe Edge Animate] Sprite画像を利用したアニメーション"></option>
<option id="30857278095" value="Adobe Edge AnimateのSymbolを使ってみる"></option>
<option id="30857271048" value="HTML5アニメーションツール「Adobe Edge Animate」のご紹介"></option>
<option id="30857275841" value="Adobe Edge Animateを使って簡単なアニメーションを作ってみる"></option>
<option id="30577164224" value="[PhantomJS]ブラウザを使わずにWebページの画面キャプチャを取る方法"></option>
</datalist>
</form>
```

##サンプルコード

- [downloads](http://ayuta-s-ooki.github.com/html5sampleworks/downloads/datalist.zip)

このサンプルでは、動的にdatalistを作成しています。
JSONPでtumblrの最新投稿リストを取得し、リストからdatalistの選択候補を作成しています。

***Javascript with HTML***

```
<script>
var tumblr = function() {};

(function(global) {

/**
 * Tumblr最新投稿リスト(JSONP)
 */
tumblr = function(resp) {
  var posts = resp.posts;
  $('#blog .loading').replaceWith('<datalist id="posts" />');
  $datalist = $('#blog datalist');
  for (var i=0; i<posts.length; i++) {
    var p = posts[i];
    var title =
      p[p.type + '-title'] || p[p.type + '-text'] || p['slug'] || 'No title';

    // 投稿リストからデータリストの作成
    $datalist.append('<option id="' + p.id + '" value="' + title + '" />');
  }

  $('input#title').on('blur', function(e) {
    $(this).trigger('focus');
  }).trigger('focus');
}

}(this));
</script>
<!-- Tumblr最新投稿リスト取得API (JSONP) -->
<script src="http://aj.ayuta.co.jp/api/read/json?callback=tumblr&amp;num=10" type="text/javascript"></script>
```


##参考

- [Specification](http://www.w3.org/TR/2011/WD-html5-20110525/the-button-element.html#the-datalist-element)
