# Rails 7.1.3 + Ruby 3.2.3 (Alpine Image)

## 環境概要
このディレクトリは、Ruby3.2.3のAlpineイメージをベースに、Rails 7.1.3アプリケーションをセットアップした環境です。  
AlpineイメージはAlpine Linuxをベースに構築されたものです。  
極めて軽量なOSになりますが、ベースとなるOSが他のイメージとは大きく異なるので、主要なパッケージ・コマンドのいくつかが無いもしくは類似の別のものを利用する必要があります。

## セットアップ手順
この環境を使用するには、以下の手順に従ってください。

1. このディレクトリ内にある `Dockerfile` と `docker-compose.yml` を使用して、Dockerイメージをビルドします。

   ```bash
   docker compose build
   ```

2. ビルドしたDockerイメージを基にコンテナを起動します。

   ```bash
   docker compose up
   ```

3. (オプション) 初回起動時には、データベースの作成やマイグレーションが必要になる場合があります。

   ```bash
   docker compose run web rails db:create db:migrate
   ```

4. コンテナを起動した後、ブラウザを通じて http://localhost:3000 にアクセスすることで、Railsアプリケーションにアクセスできます。

### Railsアプリケーションの初期化について
この環境は、次の `rails new` コマンドを使用して初期化されました：

```bash
rails new . --force --asset-pipeline=propshaft --css=sass --database=mysql
```

### 注意点
Alpineイメージを使用するため、一部の開発ツールやランタイム依存関係は手動でインストールする必要があります。  
プロジェクトの要件に応じて `Dockerfile` をカスタマイズしてください。
