#Hashchange event

hash変更のイベント通知をJavascriptで受け取ることが可能です。
hashとは、URLの末尾についている`#`から始まる文字列です。もともとは、ページ内での位置を表すアンカーの役割をします。hashが示す位置とは、hashと同じ文字列のid属性を持つ要素が該当します。
また、hash変更は、ブラウザの履歴(History API)にも登録されますので、戻る・進むボタンでこのイベントが呼ばれます。また、Javascriptで`location.hash`を書き換えることでも、同様に呼ばれます。
このイベントを使って、ページ遷移を伴わないコンテンツの書き換えを行うことが可能です。jQuery mobileやBackbone.jsなどのフレームワークなどは、これを使ってコンテンツの書き換えを行っています。(※最近では、`pushstate`を使うので、`pushstate`未サポートのブラウザの場合には、`hashchange`を使います。)

##対応状況

[Hashchange event](http://caniuse.com/#feat=hashchange)

##サンプル
このサンプルでは、リストのリンクをクリックすると、hashを切り替えます。そして、hashchange eventを受け取ると、ページ下に切り替え前のURLと切り替え後のURLが出力されます。

[Hashchange eventサンプル](http://ayuta-s-ooki.github.com/html5sampleworks/samples/hashchange/)

##サンプルコード

- [download](http://ayuta-s-ooki.github.com/html5sampleworks/downloads/hashchange.zip)

##参考

- [Specification](http://www.w3.org/TR/html5/history.html#event-hashchange)
