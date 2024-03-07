# 使用するRubyのバージョン
FROM ruby:3.2.3

# 必要なパッケージのインストール
RUN apt-get update -qq && apt-get install -y default-mysql-client

# ワーキングディレクトリの設定
WORKDIR /myapp

# 現在のディレクトリの内容をコンテナにコピー
COPY . /myapp

# Bundlerを使用してGemをインストール
RUN bundle install

# pumaサーバのポートを公開
EXPOSE 3000

