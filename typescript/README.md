# パッケージのインストール
```bash
docker-compose run --rm node yarn install
```

# 初期化
すでに追加済みだが，`src/tsconfig.json`を初期化したい時に使う
```bash
$docker-compose run --rm node yarn run tsc --init
```

# コンパイル
```
$docker-compose run --rm node yarn run build
```

# nginx 起動
```bash
$ docker-compose up
```
