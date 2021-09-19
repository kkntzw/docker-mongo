# docker-mongo
MongoDB 向けの Docker を用いた開発環境

## 前提条件
`docker`, `docker-compose` が使える環境を想定している。  
[`docker-dev`](https://github.com/kkntzw/docker-dev)の環境が構築済みであるのを想定している。  

## 環境構築
1. [当リポジトリを Clone する。](#当リポジトリを-clone-する)
1. [`docker-compose.example.yml` から `docker-compose.yml` に拡張子を変更する。](#docker-composeexampleyml-から-docker-composeyml-に拡張子を変更する)
1. [`docker-compose.yml` の環境変数を設定する。](#docker-composeyml-の環境変数を設定する)
1. [コンテナを構築する。](#コンテナを構築する)

### 当リポジトリを Clone する
```bash
cd ${任意のディレクトリ}
git clone https://github.com/kkntzw/docker-mongo.git
cd docker-mongo
```

### `docker-compose.example.yml` から `docker-compose.yml` に拡張子を変更する
```bash
mv docker-compose.example.yml docker-compose.yml
```

### `docker-compose.yml` の環境変数を設定する
```bash
vi docker-compose.yml
```

| 環境変数名 | 概要 |
| --- | --- |
| MONGO_INITDB_ROOT_USERNAME | MongoDB のユーザ名 |
| MONGO_INITDB_ROOT_PASSWORD | MongoDB のパスワード |
| USERNAME | 上記で設定したユーザ名 |
| PASSWORD | 上記で設定したパスワード |

### コンテナを構築する
```bash
docker-compose up -d --build
```

## 開発
1. [コマンドラインから操作する。](#コマンドラインから操作する)
1. [ブラウザから操作する。](#ブラウザから操作する)
1. [他コンテナから利用する。](#他コンテナから利用する)


### コマンドラインから操作する
```bash
docker-compose exec mongo mongosh --host mongo --port 27017 --username ${ユーザ名}
```

### ブラウザから操作する
[mongo.localhost](http://mongo.localhost) へアクセスする。

### 他コンテナから利用する
環境変数の `ME_CONFIG_MONGODB_URL` の値をURIとして指定する。
`mongo:27017` をURIとして指定する。
