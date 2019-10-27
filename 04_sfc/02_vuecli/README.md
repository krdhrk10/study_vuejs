# Vueの単一ファイルコンポネント導入 - vuecli v4

vue-cli v4を使用したvue appの作成手順を試す

## 概要

vue-cliはvue-cli serverによってnpmやyarn, webpackといったモジュール群をラップしたツール（と思う）
通常はvue createによってcui上でプロジェクトのセットアップが可能であるが、このチュートリアルではvue-uiを利用する。

## How to Run
```shell
$ docker build -t vuecli-devel
$ docker run -ti -v `pwd`:/root/vue -p 8080:8080 -p 8000:8000 vuecli_devel bash -c "vue ui --host 0.0.0.0"
-> このあと http://localhost:8000 にアクセス
```

上記コマンドの実行後、localhost:8000にアクセスすることでvueのプロジェクト管理UIを使用できる。  
当該UIからプロジェクトの新規作成が可能。  
  
Docker終了後、再度vue uiを起動して作業を継続する場合は、vue project manager上で既存プロジェクトのインポートが必要。  


## Note

- 内部的にどのようなwebpack設定を使用しているか知りたければ以下のコマンドを実行
  -> vue inspect

- DevTool入れるとChromeの拡張機能でVueのコンポネント情報を参照することができる
