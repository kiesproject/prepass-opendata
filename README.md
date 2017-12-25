# prepass opendata [![Build Status](https://travis-ci.org/kiesproject/prepass-opendata.svg?branch=master)](https://travis-ci.org/kiesproject/prepass-opendata)
プレまっぷで使用するオープンデータリポジトリ

## データ構造
### 本体
|要素|データ型|解説|
|:---|:-------|:---|
|`company_id`|int|企業ID|
|`shop_id`|int|店舗ID|
|`zip_code`|String|ハイフンで区切られた形式で表された店舗の郵便番号 ex.123-4567|
|`address`|String|店舗の住所|
|`building_address`|String|店舗の建物住所|
|`location`|location|店舗の位置情報のオブジェクト。詳細は[location](#location)に記載|
|`tel`|String|ハイフンで区切られた形式で表された店舗の電話番号 ex.076-123-4567|
|`fax`|String|ハイフンで区切られた形式で表された店舗のFAX番号 ex.076-123-4567|
|`url`|String|店舗・企業のウェブページ|
|`open_time`|String|店舗の開店時間|
|`close_time`|String|店舗の閉店時間|
|`pr_message`|String|店舗・企業のPRメッセージ|
|`genres`|list\<genre\>|店舗・企業のジャンルのListオブジェクト。詳細は[genre](#genre)に記載|
|`is_baby_station`|boolean|赤ちゃんのお店に加盟しているかどうか|
|`is_feed_space`|boolean|授乳室の有無|
|`is_change_diaper_space`|boolean|オムツ替えのスペースの有無|
|`is_microwave_oven`|boolean|ミルク用の電子レンジが使用可能かどうか|
|`can_buy_wet_tissues`|boolean|おむつ又はおしりふきシートの設置(販売)の有無|
|`is_boil_water`|boolean|ミルク用のお湯の有無|
|`is_child_toilet`|boolean|子供用のトイレの有無|
|`is_kids_corner`|boolean|こどもコーナーの有無|
|`is_lent_stroller`|boolean|ベビーカー貸出の有無|
|`is_child_privilege`|boolean|子供用の特典の有無|
|`is_child_menu`|boolean|子供向けメニューの有無|
|`is_no_smoking_room`|boolean|禁煙ルームの有無|
|`is_private_room`|boolean|個室の有無|
|`is_zashiki`|boolean|座敷の有無|
|`antiallergic_support`|String|小麦などのアレルギーサポートを行っている場合に入るフィールド|
|`privileges`|privileges|特典内容のオブジェクト。詳細は[privileges](#privileges)に記載|

### `location`
店舗の位置情報のデータを格納するオブジェクト、 **お店が物理的に存在しない場合、Nullが入る可能性があります** 。

|要素|データ型|解説|
|:---|:-------|:---|
|`lat`|double?|緯度|
|`lon`|double?|経度|

### `genre`
店舗のジャンルを格納するオブジェクト。
オープンデータ側で「その他」というジャンルが付いているお店はどの大ジャンルに属しているか不明なため、ジャンルなしとなっている場合があります。

|要素|データ型|解説|
|:---|:-------|:---|
|`big_genre`|String|大ジャンル。大ジャンルには食べる、買う、遊ぶ、暮らす、育てるの5つのどれかが入ります。|
|`genre`|String|小ジャンル。小ジャンルには大ジャンルの中の小さな区分にわけられたジャンルが入ります。|

#### ジャンル構成
Prepassのジャンル構成には以下のリストを用いています。

- 食べる
    - イタリアン・フレンチ
    - カレー
    - 中華・ラーメン
    - 洋食・西洋料理
    - 居酒屋
    - 和食・寿司
    - 焼肉・鉄板焼き
    - ファミレス・ファストフード
    - カフェ・スイーツ
- 買う
    - 食品
    - 日用品
    - 衣類
    - 学習用品
    - 住宅・不動産
    - 自動車
 - 遊ぶ
    - 体験・観光スポット
    - アミューズメント
    - 宿泊・温泉
    - 公園
 - 暮らす
    - 金融
    - 保険
    - 法律
    - 情報・通信
    - 交通・燃料
    - 理美容
    - 写真
    - 清掃・クリーニング
    - 健康
    - 病院
 - 育てる
    - 習い事
    - 幼稚園・保育所
    - 放課後児童クラブ
    - 児童館
    - 認可外保育所等
    - 障害者に関する児童福祉等施設
    - つどいの広場・子育て支援センター
    - 母子保健・児童福祉担当課

### `privileges`
特典内容が格納されたオブジェクト

|要素|データ型|解説|
|:---|:-------|:---|
|`two_children`|String|2人用の特典内容。特典がない場合は中身が0のStringが返却されます。|
|`three_children`|String|3人用の特典内容。特典がない場合は中身が0のStringが返却されます。|

### サンプル
```cson
[
  {
    "company_id": 123,
    "shop_id": 1,
    "shop_name": "株式会社 新宅石油店",
    "zip_code": "929-0325",
    "address": "石川県河北郡津幡町加賀爪リ11番地",
    "building_address": "",
    "location": {
      "lat": 36.6682213,
      "lon": 136.73546869
    },
    "tel": "076-289-2088",
    "fax": "076-289-2088",
    "url": "http://www.keepercoating.jp/proshop/ishikawa/city858/05018/"
    "open_time": "7:00~20:00 祝日8:00~18:00",
    "close_time": "日曜日",
    "pr_message": " 清潔な車内空間をご提案します。ジュースがこぼれた、嘔吐、におい、殺菌、お気軽にご相談ください。",
    "genres": [
      {
        "big_genre": "暮らす",
        "genre": "交通・燃料"
      },
      {
        "big_genre": "暮らす",
        "genre": "清掃・クリーニング"
      }
    ],
    "is_baby_station": false,
    "is_feed_space": false,
    "is_change_diaper_space": false,
    "is_microwave_oven": true,
    "can_buy_wet_tissues": false,
    "is_boil_water": true,
    "is_child_toilet": false,
    "is_kids_corner": false,
    "is_lent_stroller": false,
    "is_child_privilege": false,
    "is_child_menu": false,
    "is_no_smoking_room": false,
    "is_private_room": false,
    "is_zashiki": false,
    "antiallergic_support": "",
    "privileges": {
      "two_children": "",
      "three_children": "ガソリン、軽油、灯油が店頭看板から−3円/L(ポンタカード併用、クレジッド、法人不可)\n洗車、コーティング、車内クリーニング、オイル交換などの商品が通常価格から10%OFF"
    },
    "last_update": "2017-11-27T18:43:53+0900"
  },
  # ...
]
```

## LICENSE
### オープンデータ
Copyright (c) 子育てにやさしい企業推進協議会

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/">
<img alt="クリエイティブ・コモンズ・ライセンス" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a>

このリポジトリで使用しているオープンデータは[クリエイティブ・コモンズ 表示 4.0 国際 ライセンス](http://creativecommons.org/licenses/by/4.0/)の下に子育てにやさしい企業推進協議会より提供されています。
