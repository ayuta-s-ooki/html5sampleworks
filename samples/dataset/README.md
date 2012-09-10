#dataset & data-* attributes

HTML5で追加されたカスタムデータ属性を使うと、そのサイト自身が使用する独自データを格納することが可能です。この属性を使ってリストを並べ替えたり絞り込みをしたりできます。Twitterのリスト要素を見てみるとカスタムデータ属性を使っていることがわかります。(※下記はプロモーションTweetのHTML要素)

- `data-item-id`
- `data-item-type`

```
<div class="js-stream-item stream-item stream-item expanding-stream-item" data-item-id="244181421260935169-promoted" data-item-type="tweet" id="stream-item-tweet-244181421260935169-promoted" style="margin-top: 0px; ">
```

##対応状況

[dataset & data-* attributes](http://caniuse.com/#feat=dataset)

##API

指定した要素の`data-*`属性にアクセスすることができます。
`dataset`につづけて、`*`の部分をキャメルケースで指定することで個別の属性にアクセスすることが可能です。

```
element.dataset
```

例:
```
<!-- HTML -->
<div id="user" data-id="1234"></div>
<!-- Javascript -->
<script>
var element = document.getElementById('user');
var userId = element.dataset.id; // -> 1234
element.dataset.id = '5678';
userId = element.dataset.id; // -> 5678
</script>
```

##サンプル
div要素にセットしたカスタムデータ属性を取得し画面上に表示します。また、指定したカスタムデータ属性の変更を行うと表示更新します。

##サンプルコード

セットしたカスタムデータ属性は下記の通りです。

```
<div data-username="john" data-uid="1234" id="user" data-date-of-birth="1970-01-01"></div>
```

Javascriptのdataset API

```
(function(global) {
  var userElem = document.getElementById('user'),
      nameElem = document.getElementById('username'),
      idElem = document.getElementById('uid'),
      dateOfBirthElem = document.getElementById('dateOfBirth'),
      dataKeys = document.getElementById('dataKeys'),
      dataValue = document.getElementById('dataValue'),
      dataBtn = document.getElementById('dataBtn');

  // カスタムデータ属性を取得して表示
  function updateData() {
    nameElem.innerHTML = userElem.dataset.username;
    idElem.innerHTML = userElem.dataset.uid;
    dateOfBirthElem.innerHTML = userElem.dataset.dateOfBirth;
  }

  dataBtn.addEventListener('click', function(e) {
    var index = dataKeys.selectedIndex,
        val = dataValue.value;
    if (val.length > 0) {
      var key = dataKeys.options[index].value;
      // カスタムデータ属性変更
      userElem.dataset[key] = val;
      // 表示更新
      updateData();
    }
  }, false);

  updateData();
}(this));
```

##参考

[カスタムデータ属性](http://www.html5.jp/tag/attributes/data.html)

