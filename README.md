# 日野市公園マップ (Hino City Park Map)
日野市内の公園を地図上で閲覧できるインタラクティブなWebマップです。 Leaflet.jsを使用し、日野市のオープンデータを可視化しています。公園の場所、設備や遊具を確認することができます。

## 🌐 デモ (Demo)
• 公開URL: [日野市公園マップ](https://hino-park-map.web.app/)  
  　
## ✨ 特徴 (Features)
+ 公園の可視化: 市内の公園を地図上にピンで表示。
+ 詳細情報の表示: ピンをクリックすると、設備、住所がポップアップ表示されます。
+ クラスタリング機能: 「高幡不動駅」周辺など、ピンが密集している地域では自動的にグループ化（クラスタリング）され、地図が見やすくなっています。
+ 現在地表示: GPS機能を使用し、現在地周辺の文化財を探すことができます。
+ データ分離設計: 地図データは data.geojson として独立しており、データの追加・修正が容易です。  
  　
## 🛠 使用技術 (Tech Stack)
+ HTML5 / CSS3
+ JavaScript (ES6)
+ Leaflet.js (v1.9.4) - 地図描画ライブラリ
+ Leaflet.markercluster - マーカーのクラスタリングプラグイン
+ GeoJSON - 地理空間データのフォーマット
+ Firebase Hosting - 静的ホスティングサービス  
  　
## 📂 ファイル構成 (File Structure)
ソースコードの構成はシンプルに保たれています。  
.  
├── index.html      # メインの地図アプリ（Leafletの読み込みとロジック）  
├── parks.geojson    # 地図のデータファイル（緯度経度、名称、設備など）  
├── firebase.json   # Firebase Hostingの設定ファイル  
├── .gitignore      # Git管理除外設定  
└── README.md       # プロジェクトの説明書（本ファイル）  
  　
## 🚀 ローカルでの実行方法 (Development)
このプロジェクトは外部ファイル（GeoJSON）を読み込むため、ローカルで単にHTMLファイルを開いただけではブラウザのセキュリティ制限（CORS）により動作しない場合があります。以下のいずれかの方法でローカルサーバーを立ち上げて確認してください。  

+ 方法1: Firebase CLIを使用する場合（推奨）  
Firebaseプロジェクトが設定済みの環境であれば、エミュレータを使用できます。  
firebase emulators:start --only hosting  
表示されたローカルURL（例: http://localhost:5000）にアクセスします。  
  　
+ 方法2: VS Code Live Serverなどを使用する場合  
Visual Studio Codeの拡張機能「Live Server」などを利用して index.html を開いてください。  
  　
## 📊 データの更新方法 (Data Update)
データを追加・修正する場合は、index.html を編集する必要はありません。 parks.geojson ファイルを以下の形式で編集してください。  
```data.geojson
{  
  "type": "Feature",  
  "geometry": {  
    "type": "Point",  
    "coordinates": [経度, 緯度]  // 注意: Leaflet(緯度,経度)とは順序が逆です  
  },  
  "properties": {
    "name": "公園の名前",
    "type": "種別",
    "address": "住所",
    "desc": "設備・遊具",
    "marker_type": "park"
  }
}
```
  　
## 🌍 データ出典 (Data Source)
本アプリケーションで使用している公園データは、以下のオープンデータを利用・加工しています。  
• データ元: 日野市指定文化財一覧  
• ライセンス: クリエイティブ・コモンズ 表示 4.0 国際 ライセンス (CC BY 4.0)  
  
• 提供: 日野市 (Hino City)
📜 ライセンス (License)
This project is open source and available under the MIT License.
