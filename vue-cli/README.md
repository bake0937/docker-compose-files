1. 以下を実行し、vueプロジェクトを作成
```bash
$ docker-compose build --no-cache
$ docker-compose run --rm --service-ports service名 vue create .
```

2. `.prettierrc.js`と`stylelint.config.js`をvueプロジェクトへ移動する

3. VSCode の Default Formatter を`dbaeumer.vscode-eslint`に設定する

4. `.vscode/settings.json`でvueプロジェクト名を設定し，ESLintが機能するようにする

```diff
++  // ルートディレクトリではなく，サブディレクトリにvueプロジェクトを作成する場合は設定する
++  // "eslint.workingDirectories": [
++  //   "./サブディレクトリ名"
++  // ],
```

もしくは，`package.json`や`.eslintignore`等のファイルを手がかりに workingDirectories となるディレクトリを自動で設定されるようにする

```diff
{
++  "eslint.workingDirectories": [{ "mode": "auto" }]
}
```

5. `.eslintrc.js`で`eslint-plugin-vue`が機能するようにする

```diff
  extends: [
    'plugin:vue/essential',
++  'plugin:vue/recommended',
    'eslint:recommended',
    '@vue/typescript/recommended',
    '@vue/prettier',
    '@vue/prettier/@typescript-eslint',
  ],
```

6. コンテナーを起動する
```bash
$ docker-compose up
```
