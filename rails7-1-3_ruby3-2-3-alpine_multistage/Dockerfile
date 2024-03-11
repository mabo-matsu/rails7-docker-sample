FROM ruby:3.2.3-alpine as base
ARG BUNDLE_ROOT=/usr/local/bundle
ENV APP_ROOT /myapp
WORKDIR $APP_ROOT
RUN apk add --update --no-cache mysql-dev tzdata gcompat git

FROM base as bundle
RUN apk add --update --no-cache build-base
COPY Gemfile $APP_ROOT/Gemfile
COPY Gemfile.lock $APP_ROOT/Gemfile.lock
RUN bundle install -j4 && rm -rf $BUNDLE_ROOT/cache/*

FROM base
COPY . $APP_ROOT
COPY --from=bundle $BUNDLE_ROOT $BUNDLE_ROOT
EXPOSE 3000

