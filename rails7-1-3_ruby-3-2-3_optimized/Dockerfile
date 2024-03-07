FROM ruby:3.2.3

# 必要なパッケージのインストール
RUN apt-get update -qq && apt-get install -y default-mysql-client

WORKDIR /myapp

COPY Gemfile /myapp/Gemfile
COPY Gemfile.lock /myapp/Gemfile.lock

RUN bundle install

COPY . /myapp
