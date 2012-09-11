#CSS3 calc()
##対応状況

[calc()](http://caniuse.com/#feat=calc)

##サンプル
サンプルは、calc()を使ってボックスの幅を拡大しています。

```
<div id="normal">normal</div>
<div id="calc">calc</div>
<div id="sassAdd">Sass Add</div>
```

##サンプルコード

**SCSS**

```
@charset "UTF-8";

@import "compass";
@import "settings";

// CSS3 calc()ミックスイン
@mixin calc($property, $expression) {
  #{$property}: -moz-calc(#{$expression});
  #{$property}: -o-calc(#{$expression});
  #{$property}: -webkit-calc(#{$expression});
  #{$property}: calc(#{$expression});
}

// 共通のボックスサイズ
$boxWidth: 50px;
$boxHeight: 50px;

/* 共通のボックスサイズを設定 */
#normal,
#calc,
#sassAdd {
  width: $boxWidth;
  height: $boxHeight;
  border: 1px solid black;
  margin: 5px;
}

/* 元のまま */
#normal {
  background-color: lime;
}

/*
 * CSS3 calc()を使用して異なる単位でサイズを拡大
 *    calc($boxWidth + 1em);
 */
#calc {
  @include calc(width, '#{$boxWidth} + 1em');
  background-color: red;
}

/*
 * SASSの計算式でサイズを拡大(同一単位の加算か掛け算)
 *    $boxWidth(px) + 50px;
 */
#sassAdd {
  color: white;
  width: $boxWidth + 50px;
  background-color: blue;
}
```

***CSS***

```
@charset "UTF-8";
/* 共通のボックスサイズを設定 */
/* line 21, ../sass/main.scss */
#normal,
#calc,
#sassAdd {
  width: 50px;
  height: 50px;
  border: 1px solid black;
  margin: 5px;
}

/* 元のまま */
/* line 29, ../sass/main.scss */
#normal {
  background-color: lime;
}

/*
 * CSS3 calc()を使用して異なる単位でサイズを拡大
 *    calc($boxWidth + 1em);
 */
/* line 37, ../sass/main.scss */
#calc {
  width: -moz-calc(50px + 1em);
  width: -o-calc(50px + 1em);
  width: -webkit-calc(50px + 1em);
  width: calc(50px + 1em);
  background-color: red;
}

/*
 * SASSの計算式でサイズを拡大(同一単位の加算か掛け算)
 *    $boxWidth(px) + 50px;
 */
/* line 46, ../sass/main.scss */
#sassAdd {
  color: white;
  width: 100px;
  background-color: blue;
}
```

##参照

- [Specification](http://www.w3.org/TR/css3-values/#calc-notation)
