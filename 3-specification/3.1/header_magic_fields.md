#### 3.1.2 マルチブート2ヘッダのマジック領域
- magic
```
magicはヘッダを識別するマジックナンバーで，これは16進値で0xE85250D6である必要があります．
```

- architecture
```
architectureはCPUの命令セットアーキテクチャを指定します．
magicでエンディアンが指定されているので，エンディアンのみが異なるISAは同じIDとなります．
'0'は32bitの(プロテクトモードの)i386，'4'は32bitのMIPSを意味します．
```

- header_length
```
マジック領域も含めたマルチブート2ヘッダの長さをバイト単位で指定します．
```

- checksum
```
checksumは32bitの符号なしの値で，
他のマジック領域(magic，architecture，header_lengthなど)
と加算した時，32bitの符号なしの合計がゼロになる必要があります．
checksum = - (magic + architecture + header_length)
```
