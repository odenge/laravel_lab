# 概要

```
DockerにLaravelをインストールしたのみの
シンプルなLaravelのテスト環境
```

# 環境変数設定ファイル

```
Dockerの環境変数設定ファイル
/.env

Laravelの環境変数設定ファイル（コピー元）
/laravel_app/.env.example
　↓　コピーして作成する
/laravel_app/.env
```

# git clone してから動かすまでの手順

```
■「dockerのwebサーバーに入る」
docker-compose exec web bash

ディレクトリ移動
cd laravel_app

vendorディレクトリ無いのでインストール
一つ上の階層に「composer.phar」は存在する
php ../composer.phar install

/laravel_app/.envを作成
cp .env.example .env

/laravel_app/.envを下記の内容に一部変更　※「DB_HOST」は「db」とし「DB_PORT」は「3306」であることを注意
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=testdb
DB_USERNAME=root
DB_PASSWORD=rootpassword

キー作成
php artisan key:generate

キャッシュクリア
php artisan config:clear
```







# サイトURL

```
http://localhost:50012/
```




# データベース接続ツール設定

```
ホスト: 127.0.0.1
ユーザー名: root
パスワード: rootpassword
データベース: testdb
ポート: 50013
```




# Dockerイメージ

```
https://hub.docker.com/_/php
```




# Dockerコマンド

コンテナ作成と起動
```
docker-compose up -d
```

ログの確認  
（すぐにDBに接続できなかった時は、動きが止まるまで待つ）
```
全体のログ
docker-compose logs -f

Webサーバーのログ
docker-compose logs -f web
```

Webサーバーに入る
```
docker-compose exec web bash
```

サービスの停止
```
docker-compose stop
```

コンテナとネットワークの削除
```
docker-compose down
```

コンテナの状態確認
```
作業ディレクトリ内
docker-compose ps

PC全体
docker ps -a
```




# Dockerfileの修正後

```
docker-compose down
docker-compose build
docker-compose up -d
```
