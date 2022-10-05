# ファイルパス関連

## 絶対パスを表示するスクリプト

下記を適当なファイルに保存して実行可能。
$() の中身はbashによって解釈され、実行後の標準出力の文字列に置き換わる、というイメージ。
＄（）はバッククオートでも同様である。　ただし、$() の場合は、下記のように括弧中身にさらに$() を記述することができる。


```bash
#!/bin/bash

if [ $# -ne 1 ]
then
  echo "Usage : $0 [relative path]"
  exit 0
fi

path=$1

abspath=$(cd $(dirname $path) && pwd)/$(basename $path)
echo ${abspath}

```

## 
