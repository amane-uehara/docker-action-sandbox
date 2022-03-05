# pushでビルドくん

gitで`v1.0.0`のようなタグをつけて`push`すると、
GitHub ActionのCI/CDが発動し、`hello.c`がビルドされ、生成物がアップロードされるやつ。

### 使用法

`v1.0.0`のようなタグをつけてGitHubに`push`すれば、ビルドが走る。

```sh
$ git clone git@github.com:amane-uehara/push-de-build-kun.git
$ cd push-de-build-kun
$ git tag v1.0.0
$ git push --set-upstream origin v1.0.0
```

実行の詳細は

<https://github.com/amane-uehara/push-de-build-kun/actions>

から確認できる。
また生成物は

<https://github.com/amane-uehara/push-de-build-kun/releases>

に設置される。

### ビルドコマンドの変更

`main.yml`のシェルコマンドを適当に書き換える。

<https://github.com/amane-uehara/push-de-build-kun/blob/master/.github/workflows/main.yml#L16,L21>

```sh
gcc hello.c
./a.out . a.txt
pwd  >> a.txt
ls   >> a.txt
date >> a.txt
gzip a.txt
```

### LICENSE

MIT
