FROM ruby:3.2.3-slim as base
ARG BUNDLE_ROOT=/usr/local/bundle
ENV APP_ROOT /myapp
WORKDIR $APP_ROOT
RUN apt-get update -qq && apt-get install -y default-mysql-client git

FROM base as bundle
RUN apt-get install -y build-essential default-libmysqlclient-dev
COPY Gemfile $APP_ROOT/Gemfile
COPY Gemfile.lock $APP_ROOT/Gemfile.lock
RUN bundle install -j4 && rm -rf $BUNDLE_ROOT/cache/*

FROM base
COPY . $APP_ROOT
COPY --from=bundle $BUNDLE_ROOT $BUNDLE_ROOT
EXPOSE 3000

