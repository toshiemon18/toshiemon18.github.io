---
title: NeoVimに移行した
date:  2017-08-18
tags:
  - Vim
  - Programming
---

## NeoVimに移行した
Atomにvim-mde-plusやvim-surround等入れて頑張ってたけど限界だったのでNeoVimにしちゃえということで導入した。</br>
忘備録的な感じで導入の仕方をまとめておく（Macでやったので大した事ない） 。</br>
蛇足でUniteからDenite、NeocompleteからDeopleteに移行した話も書いておく。</br>

## NeoVimのインストール
Macなのでhomebrew使ってチャチャっと済ます
```shell
brew install neovim/neovim/neovim
```
そしたらなんか色々表示してくれるので、その通りにしたりする。</br>
このとき、NeoVimの設定ファイルを置いたりするディレクトリは``` $XDG_CONFIG_HOME ```という環境変数によって変えることが出来る。デフォルトは``` ~/.config/nvim ```になっているっぽい。

## 各種設定
自分はシンボリックリンク貼らずに現在のVimの設定ファイルをまとめているディレクトリからcpコマンドでコピーした。</br>
ちなみにディレクトリ構成はこんな感じ。NeoVimはinit.vimを最初に読み込むので、deinの設定はこの中に書いておいた。各種設定は各自のお好みでよしなに書いて欲しい。</br>
NeoVim導入を機にvimrcの整理と更新も出来たのでよかった。</br>
```
.config/nvim
  |-- init.vim
  |-- color
  |    |-- monokai.vim
  |-- dein                        # deinでインストールしたプラグインが入ってる
  |-- dein_files
  |    |-- dein_plugs.toml
  |    |-- dein_plugs_lazy.toml
  |-- ftplugins                   # ファイルの種類別に設定を書いておく場所
  |-- userautoload                # NeoVimの基本設定とかプラグインの設定を置く場所
```
以下のリポジトリで設定ファイルを管理している。
[https://github.com/toshiemon18/nvimrc](https://github.com/toshiemon18/nvimrc)

## UniteからDeniteへの移行
Uniteから[Denite](https://github.com/Shougo/denite.nvim)への移行について触れる。
> Dark powered asynchronous unite all interfaces for Neovim/Vim8 </br>

暗黒美夢王謹製のプラグインで、Unite.vimが暗黒の力を手に入れたため高速になったらしい。
僕の場合は``` dein_files/dein_plugs.toml ```に以下のコードを追加した。
```toml
[[plugins]]
repo = "Shougo/denite.nvim"
```
次に、DeniteはPython3を使うので、自分の環境で``` which python3 ```などしてそのPATHを設定ファイルの何処かに次のように記述しておく。
```vim
let g:python3_host_prog =expand('/path/to/your/python')
```
Deniteの設定は適当にググって自分の好きなように書けばおk。たぶんUniteと同じノリでイケるはず。 </br>

## NeocompleteからDeopleteへの移行
Neocompleteから[Deoplete](https://github.com/Shougo/deoplete.nvim)への移行についても触れる。
> Dark powered asynchronous completion framework for neovim</br>

こちらもやはり暗黒美夢王謹製のプラグイン。Deopleteは自動補完のフレームワークで、sourceと呼ばれる各言語の補完システムを導入することでそれぞれの言語の補完を実現するらしい。
こちらもPython3を使うが、Deniteのところで設定したので問題ナッシング。</br>
[ここ](https://github.com/Shougo/deoplete.nvim/wiki/Completion-Sources)にそのsourceがまとまってるので必要な言語のsourceをインストールすればおk。</br>
Denite同様にtomlに以下を追加した。
```toml
[[plugins]]
repo ="Shougo/deoplete.nvim"
```

## おわり
上記やって適当に設定書いていい感じになったのでNeoVim使っていき！