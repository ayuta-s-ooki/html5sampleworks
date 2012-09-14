#Geolocation

無線LAN・WiFi・携帯電話基地局・GPS・IPアドレスなどから位置情報を取得します。Webアプリケーションは、ブラウザーを実行している PC の現在の地理的位置情報にアクセスできます。それによって、地図上の位置を示したり、天気やニュースなどの最新のローカル情報を表示したりできます。

##対応状況

[Geolocation](http://caniuse.com/#feat=geolocation)

##API/構文

```
[NoInterfaceObject]
interface NavigatorGeolocation {
   // 現在地取得成功時のcallback引数に渡されるオブジェクト
   readonly attribute Geolocation geolocation;
};

Navigator implements NavigatorGeolocation;

[NoInterfaceObject]
interface Geolocation {
   // 現在地取得: navigator.geolocation.getCurrentPosition
   void getCurrentPosition(PositionCallback successCallback,
                           optional PositionErrorCallback errorCallback,
                           optional PositionOptions options);
   // 定期監視: navigator.geolocation.watchPosition
   long watchPosition(PositionCallback successCallback,
                      optional PositionErrorCallback errorCallback,
                      optional PositionOptions options);
   // 定期監視を停止する: navigator.geolocation.clearWatch
   void clearWatch(long watchId);
 };

 callback PositionCallback = void (Position position);

 callback PositionErrorCallback = void (PositionError positionError);
 
```

***構文***

```
function success(position) { /* 成功時の処理 */ }
function error(error) { /* 失敗時の処理 */ }

// 現在地の取得
navigator.geolocation.getCurrentPosition(success, error);

// 定期監視
var watchId = navigator.geolocation.watchPosition(success, error);
// 定期監視の停止
navigator.geolocation.clearWatch(watchId)

```

##サンプル
サンプルは、ページ読み込み時に`navigator.geolocation.getCurrentPosition`で現在地情報を取得しGoogle Mapを表示しています。また、ボタンにより`navigator.geolocation.watchPosition`を開始し、`navigator.geolocation.clearWatch`により監視を停止しています。

[Geolocationサンプル](http://ayuta-s-ooki.github.com/html5sampleworks/samples/geolocation/)

##サンプルコード

- [download](http://ayuta-s-ooki.github.com/html5sampleworks/downloads/geolocation.zip)

##参考

- [Specification](http://www.w3.org/TR/geolocation-API/)
