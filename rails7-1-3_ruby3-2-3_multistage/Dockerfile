# 使用するRubyのバージョン
FROM ruby:3.2.3 as base
ARG BUNDLE_ROOT=/usr/local/bundle
ENV APP_ROOT /myapp
WORKDIR $APP_ROOT

FROM base as bundle
COPY Gemfile $APP_ROOT/Gemfile
COPY Gemfile.lock $APP_ROOT/Gemfile.lock
RUN bundle install -j4 && rm -rf $BUNDLE_ROOT/cache/*

FROM base
COPY . $APP_ROOT
COPY --from=bundle $BUNDLE_ROOT $BUNDLE_ROOT
EXPOSE 3000

