## iOSでタイムラインの実装パターン

| パターン                 | メリット                  |  デメリット |
|:------------------------|:------------------------|:---------------------------|
| UICollectionView [^1]   | 一般的なやり方。実装量少ない | iOS５で動かない              |
| UIScrollView + 独自実装  | スクロールの動きは標準      | セルの再利用など、自前実装が必要         |
| UITableView   　　　　　　| 実装量少ない | 列が1個しかつくれない。iPad対応などで要求仕様に対応することが困難になる可能性あり              |
| UIView + 独自実装        | iOS5でも動く              | スクロールの動きが標準と異なる。独自実装が大量になる  |


[^1] UICollectionViewを使った場合にスクロールがカクツク場合は以下を参考

- [オートレイアウトの設定みなおし](http://qiita.com/yuya_presto/items/08b0656f67a59c8c2d03)
- [影・角丸の描画処理を見直す](http://d.hatena.ne.jp/shu223/20121124/1355146393)
- [Appleドキュメント](https://developer.apple.com/jp/documentation/iPhoneAppProgrammingGuide.pdf)
- [FastImageCache](https://github.com/path/FastImageCache)


## タイムライン実装例

### UICollectionViewタイプ

#### [TimelineLayout](https://github.com/seedante/TimelineLayout)
<img src="https://github.com/seedante/TimelineLayout/blob/master/Timeline-Layout-I-Screenshot.jpg" width="280px">
- スター数13 2015年12月時点, 2015年12月初回コミット, cocoacontrolsに掲載なし
- Swift製
- 見た目がいわゆるタイムライン
- ページングではなく、純粋なスクロール
- これをページングタイプにしたいなら、ページングコンテナを下に置きその上にこれを乗せる




### UIScrollView + UIViewタイプ
#### [Timeline](https://github.com/edekhayser/Timeline)
<img src="https://github.com/edekhayser/Timeline/blob/master/Screenshot.png" width="240px">
- スター数410 2015年12月時点, 2014年7月初回コミット, cocoacontrolsに掲載あり
- Swift製
- 見た目がいわゆるタイムラインだけど、一度に表示できる数は7日〜1ヶ月分程度
- それ以上のUIView一度にaddするとなると、セルの再利用しない限り重さがでてくる。
- ページングで7日単位で切り替えるという仕様なら、このOSSでも使えるが、365日滑らかなスクロールでという仕様は満たせない


### UICollectionViewタイプ 高機能

#### [INSElectronicProgramGuideLayout](https://github.com/inspace-io/INSElectronicProgramGuideLayout)
<img src="https://raw.githubusercontent.com/inspace-io/INSElectronicProgramGuideLayout/master/Screens/screen.png" width="280px">
- スター数382 2015年12月時点, 2014年12月初回コミット, cocoacontrolsに掲載あり
- Objective-C製
- スクロール時のヘッダー部分固定など技術的に難しいことをしている
- 大量データ時の工夫も入っているが、それでも量が増えてくると重い




### UICollectionViewタイプ タイルサイズが異なるもの混在

#### [NVBnbCollectionView](https://github.com/ninjaprox/NVBnbCollectionView)
<img src="https://raw.githubusercontent.com/ninjaprox/NVBnbCollectionView/master/Demo-portrait.gif" width="240px">
- スター数164 2015年12月時点, 2015年5月初回コミット, cocoacontrolsに掲載あり
- Objective-C製



### その他は、以下を「CollectionView」で検索
- https://www.cocoacontrols.com/search?q=collectionview
- https://github.com/search?utf8=%E2%9C%93&q=collectionview
