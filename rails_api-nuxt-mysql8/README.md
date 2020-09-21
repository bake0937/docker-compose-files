
# `.env`を利用する
※あくまでテンプレート用に`.env`をバージョン管理しているだけで開発で使用する際は`.env`を`.gitignore`で除外する
```diff
$ pwd
rails_api-nuxt-mysql8
mv .env.dev .env
```

# RailsAPIプロジェクトを作成

```bash
$ docker-compose run --no-deps --rm backend rails new . --force --api --database=mysql --skip-bundle
```

# `database.ymlを編集する`
`.env`を読み込むようにする
```diff
# backend/config/database.yml
--password:
--host: localhost
++password: <%= ENV['MYSQL_ROOT_PASSWORD'] %>
++host: db
```

# gem "dotenv-rails" をインストールする
```diff
#Gemfile
group :development, :test do
  # Call 'byebug' anywhere in the code to stop execution and get a debugger console
  gem 'byebug', platforms: [:mri, :mingw, :x64_mingw]

++gem "dotenv-rails"
end
```

# `create-nuxt-app`でNuxt.jsプロジェクトを作成

```bash
$ docker-compose run --rm frontend npx create-nuxt-app frontend
```

forntendディレクトリ直下に移動する
```bash
$ mv frontend/frontend/{*,.[^\.]*} frontend
$ rm -r frontend/frontend
```

ディレクトリを移動させたため`yarn install`し直す
```bash
$ docker-compose run --rm --service-ports frontend yarn install
```

# 各コンテナーを起動しアプリを起動する
RailsAPIプロジェクトで作成した時のVolumeは削除する
```bash
$ docker-compose down --volume
```
DBを作成
```bash
$ docker-compose run --rm backend bundle install
$ docker-compose run --rm --service-ports backend rake db:create
```
RailsAPI、Nuxt.js、DBコンテナーを起動する
```bash
$ docker-compose up
```
