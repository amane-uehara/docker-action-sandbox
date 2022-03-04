# pushでビルドくん

gitで`v1.0`のようなタグをつけて`push`すると、
GitHub ActionのCI/CDが発動し、ビルド生成物がアップロードされるやつ。

pushでビルドしたいリポジトリに、ファイルを1つ追加すれば動く。
めちゃくちゃ簡単。

### 準備

例として

<https://github.com/yourname/repo>

のリポジトリにビルド機能を付けたいとする。
この場合

<https://github.com/amane-uehara/docker-action-sandbox/blob/master/.github/workflows/main.yml>

の`main.yml`を、
<https://github.com/yourname/repo>
以下の

```
.github/workflows/main.yml
```

にコピーすればOK。

### ビルドコマンドの設定方法

`main.yml`のシェルコマンドを適当に書き換えて使う。

<https://github.com/amane-uehara/docker-action-sandbox/blob/master/.github/workflows/main.yml#L14,L20>

```sh
echo "Hello, world!" > a.txt
pwd  >> a.txt
ls   >> a.txt
date >> a.txt
gzip a.txt
```

ここでは例として`a.txt.gz`を作っている。

### 使用法

`v1.0`のようなタグをつけてGitHubに`push`すれば、ビルドが走る。

```sh
$ git clone git@github.com:yourname/repo.git
$ cd repo
$ git tag v1.0.0
$ git push --set-upstream origin v1.0.0
```

実行の詳細は

<https://github.com/yourname/repo/actions>

から確認できる。
また生成物は

<https://github.com/yourname/repo/releases>

に設置される。

### LICENSE

MIT
