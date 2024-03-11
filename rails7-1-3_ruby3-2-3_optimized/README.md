# Rails 7.1.3 + Ruby 3.2.3 (Optimized Image)

## 環境概要
このディレクトリは、Rails 7.1.3 アプリケーションをセットアップするために、最適化された`rails new`コマンドを使用した環境です。  
使用されたRubyのバージョンは3.2.3で、以下のコマンドを利用して、不必要な機能やファイルを生成しないように最適化しました。
```bash
rails new . --force --asset-pipeline=propshaft --css=sass --database=mysql --skip-git --skip-docker --skip-action-mailer --skip-action-mailbox --skip-action-text --skip-active-job --skip-active-storage --skip-action-cable --skip-jbuilder --skip-bootsnap
```
この最適化の目的は、Dockerイメージのサイズを削減し、ビルド時間を短縮することにあります。  
しかし、`rails new`コマンドでスキップした機能に関連するGemがRails gemの依存関係としてインストールされるため、最終的なDockerイメージサイズに顕著な差は見られませんでした。

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
