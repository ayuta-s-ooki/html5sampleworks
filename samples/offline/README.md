#Online/Offline Events

オフラインに対応する良い Web アプリケーションを構築するためには、アプリケーションが実際にいつオフラインなのか知る必要があります。
`online`と`offline`イベントを使うことによりいつネットワーク状態が復旧/障害になったか検出することが可能です。
また、アプリケーション側で現在のネットワーク状態がオンラインなのか知るのに、`navigator.onLine`というプロパティでチェックすることが可能です。

##API

```
interface Navigator {
  onLine: {boolean}     // ネットワークがオンラインならtrue、オフラインならfalse
}
```

##サンプル

`navigator.onLine`と`online/offline`イベントを使って、ネットワークの状態を調べオンラインなら緑、オフラインなら赤で状態を表示します。無線LANの場合はOffにしたり、ネットワークケーブルを抜いたりして確認してみてください。(Webkit系ブラウザで動作します)

##サンプルコード

- [download](http://ayuta-s-ooki.github.com/html5sampleworks/downloads/offline.zip)


##参考

- [Online and Offline Events](https://developer.mozilla.org/ja/docs/Online_and_offline_events)
