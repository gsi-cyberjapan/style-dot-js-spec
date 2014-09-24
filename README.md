style-dot-js-spec
=================
# ベクトルタイルスタイル定義 style.js 規約
※この規約は検討中のものであり、今後変更する可能性がある。
## 適用範囲
本文書では、ベクトルタイルデータのスタイル定義を JavaScript ファイルでタイルデータセットに埋め込むための規約を示す。

## ファイルのパス
ベクトルタイルデータセット tiles に対して、style.js は下記の位置（各ズームレベルのフォルダ{z}と兄弟になる位置）に配置する。

```text
 tiles/ -+- 0/ --- 0/ --- 0.geojson
         +- 1/ -+- 0/ -+- 0.geojson
         |      |      +- 1.geojson
         |      +- ...
         +- 2/ -...
         ...
         +- style.js
```

言い換えれば、テンプレートURL http://server/theme/{z}/{x}/{t}.geojson で表現されるタイルセットのスタイル定義は、http://server/theme/style.js に置かれることとする。

JavaScript ファイルの名称は style.js をデフォルトとする。他のパスに配置した場合には、対応ソフトウェア側がそのパスを把握する必要がある。

## 規定
1. style.js は、L.TileLayer.GeoJSON のコンストラクタの第二引数 options 及び第三引数 geojsonOptions をそれぞれその名前を持つプロパティとして格納したものとする。
2. 但し、layers-dot-json-spec に基づく layers.json の規定は、style.js の定義を上書きするものとする。

## サンプル
```javascript
{
options:
{
  unique: function(feature) {
    return feature.properties.id;
  }
},
geojsonOptions:
{
  style: function(feature) {
    // ...
  },
  onEachFeature: function(feature, layer) {
    // ...
  }
}
}
```

## その他の規約
+ ファイルの文字コードはUTF-8とし、Unicodeエスケープは行わない。

## 参考文献
1. L.TileLayer.GeoJSON
