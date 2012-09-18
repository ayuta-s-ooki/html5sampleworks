#matchesSelector

`matchesSelector`は、対象要素がセレクターにマッチしているかをチェックできる機能です。jQueryの`is()`のようなことが可能です。
Selectors API v2で定義されていて、v1の時から存在する`querySelector`と`querySelectorAll`に加えて追加されている機能です。(仕様上のAPIは、`matches`になっています。)
また、jQueryでも内部的に使っているようです。

***jQuery1.7.1の例(少しコードは異なるが、jQuery1.8.1でも同じように使っていました)***

```
4045-};
4046-
4047:Sizzle.matchesSelector = function( node, expr ) {
4048-	return Sizzle( expr, null, null, [node] ).length > 0;
4049-};
--
5095-(function(){
5096-	var html = document.documentElement,
           // ----- 各ブラウザで実装されている`matchesSelector`を格納
5097:		matches = html.matchesSelector || html.mozMatchesSelector || html.webkitMatchesSelector || html.msMatchesSelector;
5098-
5099-	if ( matches ) {
5100:		// Check to see if it's possible to do matchesSelector
5101-		// on a disconnected node (IE 9 fails this)
5102-		var disconnectedMatch = !matches.call( document.createElement( "div" ), "div" ),
--
5112-		}
5113-
5114:		Sizzle.matchesSelector = function( node, expr ) {
5115-			// Make sure that attribute selectors are quoted
5116-			expr = expr.replace(/\=\s*([^'"\]]*)\s*\]/g, "='$1']");
--
5121-						var ret = matches.call( node, expr );
5122-
5123:						// IE 9's matchesSelector returns false on disconnected nodes
5124-						if ( ret || !disconnectedMatch ||
5125-								// As well, disconnected nodes are said to be in a document
--
5416-
5417-			while ( cur ) {
5418:				if ( pos ? pos.index(cur) > -1 : jQuery.find.matchesSelector(cur, selectors) ) {
5419-					ret.push( cur );
5420-					break;
--
5545-
5546-		return elems.length === 1 ?
5547:			jQuery.find.matchesSelector(elems[0], expr) ? [ elems[0] ] : [] :
5548-			jQuery.find.matches(expr, elems);
5549-	},

```

##対応状況

[matchesSelector](http://caniuse.com/#feat=matchesselector)

##API
##サンプル
`matchesSelector`を使って、個々の要素にイベントハンドラを設定するのではなく、クリックイベントのターゲット`event.target`を`matchesSelector`で調べて、スタイルを簡単に切り替えできるようにしています。jQueryの`on()[旧live()/delegate()]`と同じような機能を実現しています。

[matchesSelectorのサンプル](http://ayuta-s-ooki.github.com/html5sampleworks/samples/matchesselector/)

##サンプルコード

- [download](http://ayuta-s-ooki.github.com/html5sampleworks/downloads/matchesselector.zip)

##参考

- [Specification](http://dev.w3.org/2006/webapi/selectors-api2/)
