#Sandbox attribute for iframes

`<iframe>`に対して、セキュリティ制限をかける機能です。同一のオリジン(スキーム://ホスト:ポート)か異なるオリジンかに関わらず、この属性によって制限をかけることが可能です。

##対応状況

[Sandbox attribute for iframes](http://caniuse.com/#feat=iframe-sandbox)

##サンプル
このサンプルでは、`sandbox`属性の組み合わせにより、iframeからのフォーム送信やスクリプト実行、ローカルストレージへのアクセスがどのような挙動になるかを確認することが可能です。
各属性の値の意味は下記の通りです。

- `allow-forms` - iframe内のフォームの送信許可。このサンプルでは、フォーム送信で`b.html`という別ページを表示しています。
- `allow-scripts` - iframe内でスクリプト実行許可。このサンプルでは、Javascriptで緑色のラベル要素の追加とローカルストレージの値の取得・表示を行っています。
- `allow-same-origin` - 親フレームと同じオリジンをもつと見なす。機能の許可というより、親と共通のデータベースAPI(ローカルストレージなどオリジン単位でデータを保存)へアクセスするのに必要
- `allow-top-navigation` - iframeから親フレーム(元の最上位のページ)のウインドウ操作を許可。このサンプルでは、`b.html`を親フレームへ表示しています。

[Sandbox attribute for iframesサンプル](http://ayuta-s-ooki.github.com/html5sampleworks/samples/iframe/)

##サンプルコード

- [download](http://ayuta-s-ooki.github.com/html5sampleworks/downloads/iframe.zip)

##参考

- [Specification](http://www.w3.org/TR/html5/the-iframe-element.html#attr-iframe-sandbox)
