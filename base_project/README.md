# ベースプロジェクト

各環境作る際の基本となるファイルを配置しています。　　
プロジェクトの初期化やDockerイメージのビルドに必要な以下のファイルが含まれています。

- Dockerfile
- docker-compose.yml
- Gemfile
- Gemfile.lock

## 初期化手順
プロジェクトのセットアップには、以下のステップに従ってください。

### 1. Dockerイメージのビルド
最初に、現在のディレクトリにある `Dockerfile` と `docker-compose.yml` を使用してDockerイメージをビルドします。
```bash
docker compose build
```

### 2. Railsプロジェクトの初期化
次に、以下のコマンドを実行してRailsプロジェクトを初期化します。  
ここでのオプションはプロジェクトの要件に合わせて適宜調整してください。
```bash
docker compose run web rails new . --force --asset-pipeline=propshaft --css=sass --database=mysql
```

このコマンドにより、アプリケーションの基本的なフォルダ構造が生成されます。  
このプロセスで `Dockerfile` や `docker-compose.yml` が上書きされることがあるため、必要に応じてこれらのファイルを再度編集する必要があります。

### 3. Dockerイメージの再ビルド
環境設定を更新した後、変更を適用するためにDockerイメージを再ビルドします。
```bash
docker compose build
```

### 4. アプリケーションの起動
最後に、以下のコマンドでDockerコンテナを起動し、Railsアプリケーションを実行します。
```bash
docker compose up
```

これらの手順に従ってセットアップを完了させることで、Railsアプリケーションの開発環境が整います。  
`slim` や `alpine` パッケージを使用する場合は、`Dockerfile` および `docker-compose.yml` の内容を適宜書き換える必要がありますのでご注意ください。
