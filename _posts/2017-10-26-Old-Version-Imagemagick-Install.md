---
title: 古いバージョンのimagemagick入れたいときの忘備録
data:  2017-10-26
tags:
  - Programming
  - Rails
---

## TL;DR
- Railsでbundle installしたらrmagickでコケる
- rmagick2.16.0 (記事時点での最新バージョン)がimagemagick7に未対応
- 過去バージョン入れればいいのはわかるけどやり方がわからん
  - ググったらやり方を見つけた

## ハマった箇所
rmagickのインストール時に以下のようなエラーが出た.

```
Can't install RMagick 2.16.0. Can't find the ImageMagick library or one of the dependent libraries. Check the mkmf.log file for more detailed information.
```
エラーメッセージでググったら以下のような記事が見つかったのでやってみた.
[mgickのインストールにハマった](https://qiita.com/ShuntaShirai/items/c582c0acebe2dbf03fc3)
解決した方法という箇所に書いてある通りimagemagick6の適当なリビジョンを探してcheckoutしたあとにbrew install imagemagickという流れでやってみたが, 7.0.7がインストールされてしまった.
しかし, comment欄にある方法で解決したのでこちらを推す

```
$ brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/6f014f2b7f1f9e618fd5c0ae9c93befea671f8be/Formula/imagemagick.rb
```

リビジョンは適当に指定すると良さそう
