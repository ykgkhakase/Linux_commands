# grep の基本的な使い方(ログ編）

grep [検索ワード] ファイル

## abinitmp.logというファイル名の中から MP2 と書いてある行を抜き出す。
```bash
$ grep "MP2" abinitmp.log
```

## abinitmp.logというファイル名の中から "## MP2-IFIE" と書いてある行を表示する。
検索ワードにスペースが含まれるので、ダブルクオートで検索ワードを括っている。

```bash
$ grep "## MP2-IFIE" abinitmp.log
```

## abinitmp.logというファイル名の中から "## MP2-IFIE" と書いてある行から10行を表示する。
-A オプションで指定可能。
逆は -B オプションを使う。
```bash
$ grep -A 10 "## MP2" abinitmp.log
```

## abinitmp.logというファイル名の中から automatic と書いてある行を表示する。
-i オプションで、この時大文字と小文字の区別をしない。

```bash
$ grep -i automatic abinitmp.log
```

-A などのオプションを組み合わせることができる。

```bash
$ grep -A 100 -i automatic abinitmp.log
```

### 複数のgrepを使ってさらに絞り込むことができる。
| パイプで grep コマンドを連結する。2個目以降のgrep にはファイル名を指定していないことに注意。

```
$ grep -A 1000  -i automatic abinitmp.log  | grep "Basic Charged"
```

