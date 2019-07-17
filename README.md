# ロボカップジュニア RoboCup Junior
### レスキュー　スコアリングシステム 環境構築用　ヘルパーファイル
これは，RCJ Scoring SystemをDockerイメージで構築する際に使用するヘルパーファイルです．

## 対応環境
Unix系環境 (Ubuntu / CentOS など)

## テスト済み環境
* Ubuntu 16.04 LTS
* Ubuntu 18.04 LTS
* Synology DiskStation DSM 6.2 (公式Dockerパッケージをインストール済み)
* macOS 10.14 Mojave

## Dockerのセットアップ
各OSによってセットアップ方法が異なります．
下のページの内容を確認して，Dockerを使用可能な状態にセットアップしてください．
または，次のコマンドを入力することで，一発でDockerがセットアップされます．
`sudo curl -sSL https://get.docker.com/ | CHANNEL=stable sh`

[https://docs.docker.com/install/](https://docs.docker.com/install/)



## セットアップヘルパーのダウンロードと実行
#### gitがシステムにインストールされていない場合は，まずこれをインストールします．
[参考] https://git-scm.com/book/ja/v2/使い始める-Gitのインストール

#### セットアップヘルパーをダウンロードします．
`git clone https://github.com/rrrobo/rcj-scoring-docker`

#### セットアップを開始します.
`cd rcj-scoring-docker`
`sudo chmod +x *.sh`
`./setup.sh`
実行の途中で，パスワードの入力を求められることがあります． 

完了したら，http://localhost:3000（他のPCからアクセスする場合は，http://IPアドレス:3000 ） にアクセスすると，既にシステムが起動しており，使用可能な状態となります．

## システムの停止
次のコマンドをセットアップヘルパーのディレクトリ(rcj-scoring-docker)の中で実行します．
`./stop.sh`
実行の途中で，パスワードの入力を求められることがあります．

## システムの再開
次のコマンドをセットアップヘルパーのディレクトリ(rcj-scoring-docker)の中で実行します．
`./start.sh`
実行の途中で，パスワードの入力を求められることがあります．

## システムの再起動
次のコマンドをセットアップヘルパーのディレクトリ(rcj-scoring-docker)の中で実行します．
`./restart.sh`
実行の途中で，パスワードの入力を求められることがあります．

## システムの最新版への更新
次のコマンドをセットアップヘルパーのディレクトリ(rcj-scoring-docker)の中で実行します．
実行すると，最新のイメージがDocker Hubからダウンロードされ，コンテナが置き換えられます．
作成した大会や競技などのデータは保持されます．
`./update.sh`
実行の途中で，パスワードの入力を求められることがあります．

更新がない場合でもコンテナの置き換えは実行されます．

## adminアカウントのパスワードの変更
adminアカウントのパスワードを変更したい場合，セットアップヘルパーのディレクトリ(rcj-scoring-docker)の中にある，`process.env` というファイルを適当なエディタで編集します．

```
# db vars see more at http://mongoosejs.com/docs/connections.html
DB_CONNECT_STR=mongodb://localhost/rcj-scoring

# web vars
WEB_HOSTPORT=3000

# log vars ERROR/INFO/DEBUG
MAIN_LOG_LVL=DEBUG

# Account hardcoded
user=admin
password=admin

# Default Account Setting
dUsername=admin
dPassword=adminpass       #ここを好きなパスワードに変更する
dAdmin=true
dSDAdmin=true
```

次のコマンドをセットアップヘルパーのディレクトリ(rcj-scoring-docker)の中で実行することで，変更が適応されます．
`./restart.sh`
実行の途中で，パスワードの入力を求められることがあります．