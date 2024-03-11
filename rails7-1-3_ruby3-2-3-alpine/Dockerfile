# 使用するRubyのバージョン
FROM ruby:3.2.3-alpine

# 必要なパッケージのインストール
RUN apk add --update --no-cache build-base mysql-dev tzdata gcompat git

# ワーキングディレクトリの設定
WORKDIR /myapp

# 現在のディレクトリの内容をコンテナにコピー
COPY . /myapp

# Bundlerを使用してGemをインストール
RUN bundle install

# pumaサーバのポートを公開
EXPOSE 3000

