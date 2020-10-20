docker-compose.yml にある`working_dir`の「プロジェクト名」の部分を作成したいプロジェクト名に変更してから実行する
```bash
$ docker-compose build
$ docker-compose run --rm react yarn create react-app .
```

コンテナーを起動する
```bash
$ docker-compose up
```
