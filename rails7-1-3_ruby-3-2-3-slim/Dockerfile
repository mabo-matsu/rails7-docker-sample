# 使用するRubyのバージョン
FROM ruby:3.2.3-slim

# 必要なパッケージのインストール
RUN apt-get update -qq && apt-get install -y build-essential default-mysql-client default-libmysqlclient-dev git

# ワーキングディレクトリの設定
WORKDIR /myapp

# 現在のディレクトリの内容をコンテナにコピー
COPY . /myapp

# Bundlerを使用してGemをインストール
RUN bundle install

# pumaサーバのポートを公開
EXPOSE 3000
