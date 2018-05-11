#### 3.1.5 マルチブート2ヘッダのアドレスタグ

|型 |メンバ|
|:--|:-----|
|u16|type = 2|
|u16|flags|
|u32|size|
|u32|header_addr|
|u32|load_addr|
|u32|load_end_addr|
|u32|bss_end_addr|

このタグの全てのアドレスメンバは物理アドレスです．
それぞれの意味は以下のようになっています．  

- header_addr
```
マルチブート2ヘッダの先頭に対応するアドレス(マジック値がロードされる物理メモリの場所)です．
このアドレスは，OSイメージのオフセットと物理メモリアドレスとの間のマッピングを同期させるのに役立ちます．
```

- load_addr
```
テキストセグメントの先頭の物理アドレスです．
OSイメージファイルの読み込みを開始するオフセットは，
ヘッダが見つかった所からのオフセット，(header_addr - load_addr)で定義されます．
load_addrはheader_addr以下でなければなりません．  

特別な値-1は，ファイルを最初からロードする必要があることを意味します．
```

- load_end_addr
```
データセグメントの末尾の物理アドレスです．
(load_end_addr - load_addr)は，どれだけのデータをロードすればよいかを指定します．
これは，テキストセグメントとデータセグメントがOSイメージ内で連続している必要があることを意味します．
これは既存のa.out実行可能フォーマットでも当てはまります．
この値が0の場合，ブートローダはOSイメージがテキストセグメントとデータセグメントだけのものとみなします．
```

- bss_end_addr
```
The boot loader initializes this area to zero,
and reserves the memory
it occupies to avoid placing boot modules and other data relevant to the operating system in that area.
bssセグメントの末尾の物理アドレスです．
ブートローダはこの領域をゼロで初期化して，
この領域にブートモジュール及び関連する他のデータを配置することを避けるため，メモリを予約します．
この値が0の場合，ブートローダはbssセグメントが存在しないとみなします．
```
