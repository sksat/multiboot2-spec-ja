#### 3.1.1 マルチブート2ヘッダのレイアウト

マルチブート2ヘッダのレイアウトは，次のようにする必要があります．

| オフセット | 型 |    領域名    | 備考 |
|:-----------|:---|:-------------|:-----|
|  0         |u32 |マジック      | 必須 |
|  4         |u32 |アーキテクチャ| 必須 |
|  8         |u32 |ヘッダ長      | 必須 |
| 12         |u32 |チェックサム  | 必須 |
| 16-XX      |    |タグ          | 必須 |

フィールド「マジック」，「アーキテクチャ」，「ヘッダ長」は
[ヘッダマジック領域](./header_magic_fields.md)
「タグ」は
[ヘッダダグ](./header_tags.md)
で定義されています．
全ての領域はネイティブのエンディアンになっています．
バイエンディアンプラットフォームでは，ネイティブのエンディアンとはOSイメージが開始するエンディアンを意味します．