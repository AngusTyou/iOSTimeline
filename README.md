## iOSでタイムラインの実装パターン

オープンソースを10個ほど調べてみたところ、UICollectionViewが8個、それ以外が2個でした。

| パターン                 | メリット                  |  デメリット |
|:------------------------|:------------------------|:---------------------------|
| UICollectionView [^1]   | 一般的なやり方。実装量少ない | iOS５で動かない              |
| UITableView   　　　　　　| 実装量少ない | 列が1個しかつくれない。iPad対応などで要求仕様に対応することが困難になる可能性あり              |
| UIView + 独自実装        | iOS5でも動く              | スクロールの動きが標準と異なる。独自実装が大量になる  |
| UIScrollView + 独自実装  | スクロールの動きは標準      | セルの再利用など、自前実装が必要         |

[^1] UICollectionViewを使った場合にスクロールがカクツク場合は以下を参考

- [オートレイアウトの設定みなおし](http://qiita.com/yuya_presto/items/08b0656f67a59c8c2d03)
- [影・角丸の描画処理を見直す](http://d.hatena.ne.jp/shu223/20121124/1355146393)
- [Appleドキュメント](https://developer.apple.com/jp/documentation/iPhoneAppProgrammingGuide.pdf)
- [FastImageCache](https://github.com/path/FastImageCache)


## 実装例

#### [TimelineLayout](https://github.com/seedante/TimelineLayout)
- スター数13 2015年12月時点, 2015年12月初回コミット, cocoacontrolsに掲載なし
- Swift製
- UICollectionView使用

![代替テキスト](画像のURL)


#### [Timeline](https://github.com/edekhayser/Timeline)
- スター数410 2015年12月時点, 2014年7月初回コミット, cocoacontrolsに掲載あり
- Swift製
- UICollectionView未使用。

<img src="https://github.com/edekhayser/Timeline/blob/master/Screenshot.png" width="width="320px">
