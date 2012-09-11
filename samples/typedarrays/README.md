#Typed Arrays

Javascriptの型付き配列で、生のバイナリデータをより効率的にアクセスする機能を提供するためにサポートされました。
音声や動画の操作、WebSockets を用いたデータのアクセスなどで使用することを想定しています。

##対応状況

[Typed Arrays](http://caniuse.com/#feat=typedarrays)

##API

バッファとビューに実装が分かれています。バッファ単独では中身にアクセスできないため、ビューを使用してバッファにアクセスします。

**バッファ**

```
[Constructor(unsigned long length)]
interface ArrayBuffer {
    unsigned long byteLength;                           // バッファのバイト長
    ArrayBuffer slice(long begin, optional long end);   // 指定された'begin'と'end'のバイトのコピーを新しいArrayBufferで返す(マイナス指定も可)
}
```

ビューはそれぞれの型を持つTyped Array viewとして定義されています。

- `Int8Array`
- `Uint8Array`
- `Uint8ClampedArray`
- `Int16Array`
- `Uint16Array`
- `Int32Array`
- `Uint32Array`
- `Float32Array`
- `Float64Array`

Typed Array viewの例:

```
var f64a = new Float64Array(8);
f64a[0] = 10;
f64a[1] = 20;
f64a[2] = f64a[0] + f64a[1];
```

##サンプル

このサンプルは、CanvasのImageDataオブジェクトの色情報(RGBA)のdataプロパティがtyped array(Uint8ClampedArray)であることを確かめています。

###その他の例

WebGLの例:

```
// WebGLのバッファオブジェクトにセット
var floatArray = new Float32Array([1,2,3,4,5,6,7,8]);
gl.bufferData(gl.ARRAY_BUFFER, floatArray);

// テクスチャーコンテンツのサンプル
var pixels = new Uint8Array(16*16*4); // 16x16 RGBA image
gl.texImage2D(
  gl.TEXTURE_2D, // target
  0, // mip level
  gl.RGBA, // internal format
  16, 16, // width and height
  0, // border
  gl.RGBA, //format
  gl.UNSIGNED_BYTE, // type
  pixels // texture data
);
```

Canvasの例:

```
var imageData = ctx.getImageData(0,0, 200, 100);
var typedArray = imageData.data // data is a Uint8ClampedArray
```

XMLHttpRequestv2の例:

```
// レスポンスデータタイプをArrayBufferにする
xhr.responseType = 'arraybuffer';
```

File APIの例:

```
// ファイルをArrayBufferとして読む
reader.readAsArrayBuffer(file);
```

WebSocketsの例:

```
socket.binaryType = 'arraybuffer';
```

##サードパーティライブラリ

- [jDataView](https://https//github.com/vjeux/jDataView)
- [stringencoding](http://code.google.com/p/stringencoding)
- [bitview.js](http://fhtr.org/shp.js/)
- [DataStream.js](http://github.com/kig/DataStream.js)

##参照

- [Specification](http://www.khronos.org/registry/typedarray/specs/latest/)

