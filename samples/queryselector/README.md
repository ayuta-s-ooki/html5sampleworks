#querySelector/querySelectorAll

`querySelector`は、与えられたCSSセレクタにマッチする文書中の最初の要素を返します。`querySelectorAll`は、与えられたCSSセレクタにマッチする文書中の要素のリストを返します。jQueryなどの隣接セレクタや階層セレクタと同じようなことがネイティブで実現できます。

##対応状況

[querySelector/querySelectorAll](http://caniuse.com/#feat=queryselector)

##API

```
partial interface Document {
    querySelector: {function(string): ?Element},    // CSSセレクタにマッチした最初の要素を返す
    querySelectorAll: {function(string): NodeList}  // CSSセレクタにマッチした要素のリストを返す
}

partial interface DocumentFragment {
    querySelector: {function(string): ?Element},
    querySelectorAll: {function(string): NodeList}
}

partial interface Element {
    querySelector: {function(string): ?Element},
    querySelectorAll: {function(string): NodeList}
}
```

##サンプル
セレクトボックスからCSSセレクタを、ラジオボタンからセレクタメソッドを選択して、マッチした要素に対して、クラス属性を付与し下記のスタイルを適用します。

```
.selected {
  background-color: pink;
}
```

##サンプルコード
- [download]()

***HTML***

```
<div id="container">
  <div id="header">
    <span class="head">header</span>
  </div>
  <div id="content">
    <div id="menu">
      <ul id="menuList">
        <li class="list item1">item1</li>
        <li class="list item2">item2</li>
        <li class="list item3">item3</li>
        <li class="list item4">item4</li>
        <li class="list item5">item5</li>
      </ul>
    </div>
  </div>
  <div id="footer">
    <span class="foot">footer</span>
  </div>
</div>
```

***Javascript***

```
(function(global) {
  var selectors = null, fnName = null;

  /**
   * 前回の結果を初期化
   */
  function reset() {
    var selected = document.querySelectorAll('.selected');
    for (var i = 0; i < selected.length; i++) {
      var elem = selected[i];
      elem.classList.remove('selected');
    }
  }

  /**
   * 選択したCSSセレクタにスタイルを適用する
   *
   * @param {string} selectors CSSセレクタ.
   * @param {string} name SelectorsAPIの関数名(querySelector, querySelectorAll).
   */
  function update(selectors, name) {
    reset();
    if (name === 'querySelector') {
      document.querySelector(selectors).classList.add('selected');
    } else {
      var elems = document.querySelectorAll(selectors);
      for (var i = 0; i < elems.length; i++) {
        elems[i].classList.add('selected');
      }
    }
  }

  // セレクターの変更
  document.getElementById('selectors').addEventListener('change', function(e) {
    if (this.value !== '') {
      selectors = this.value;
      update(selectors, fnName);
    }
  }, false);

  // querySelector選択
  document.getElementById('one').addEventListener('click', function(e) {
    fnName = this.value;
    update(selectors, fnName);
  }, false);

  // querySelectorAll選択
  document.getElementById('all').addEventListener('click', function(e) {
    fnName = this.value;
    update(selectors, fnName);
  }, false);

  // Initialize.
  global.addEventListener('load', function(e) {
    var options = document.getElementById('selectors'),
        radios = document.getElementsByName('q');
    selectors = options[0].value;
    fnName = radios[0].value;
    reset();
  }, false);
}(this));
```

##参考

- [Specification](http://www.w3.org/TR/selectors-api/)

