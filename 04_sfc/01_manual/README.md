# Vueの単一ファイルコンポネント導入 - 手動

どのモジュールが何をしているか理解するためにvue-cliを利用せずにvueのコンポネント化を試す

## 概要

vueの単一ファイルコンポネントとは、1つのファイルに1つのvueコンポネントの
見た目と機能の実装を可能にする書式仕様である。  
  
一般的に.vue拡張子がつけられ、内部に template, script, styleといった記述をもつ。  
  
この記述を可能にしているのは、webpackというバンドラーのpluginである vue-loader であり、  
これが上述のような書式を解釈して通常のhtml/css/javascriptの構造に変換する。  

## How to Run
```shell
$ docker build -t vue-devel
$ docker run -ti -v `pwd`:/root/app vue-devel npm run build
``

## Note

### npm

- 通常、node moduleの検索パスはnpm実行パス「/path/to/current」の時、以下のようになる
  - /path/to/current/node_modules
  - /path/to/node_modules
  - /path/node_modules
  - /node_modules
  - これらのどこかに配置するようにセットアップしておくとnot foundやcan't resolveでハマりにくい
- グローバルインストールについて
  - グローバルインストールした時のインストールパスは{prefix}/lib/node_modulesになる
  - 上記のパスは npm root -g で確認できる
  - prefixについては npm -g config set prefix="path/to/prefix" で設定できる
- 実行パスについて
  - node moduleの中には直接コマンド実行できるツールも含まれており、これらはpathが通った箇所に配置するのが望ましい
  - 実行できるツール類は、通常 {prefix}/bin に配置される
  - 上記パスは npm bin -g で確認できる

### webpack

- npx webpack で実行するとパス関連の問題でハマりにくい
- requireで指定するnode moduleは global.module.paths で定義されているものが指定できる
- global.module.pathsはnodeコマンドで対話的に出力するか、 node -e "console.log(global.modules)" などで参照できる
- import x from y のような記述でのmodule参照についてはなぜか global.module.paths が効かない
- webpack.config.jsonのresolve.modulesで絶対パス指定してやる必要がある
