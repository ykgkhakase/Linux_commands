# ファイルのバックアップスクリプトのサンプル集

## bashrc の手動バックアップ

ここではバックアップファイルの末尾に指定した文字列や日付を付与することで、新規のファイル名を自動で生成してコピーしている。


```bash
#!/bin/bash

if [ $# -eq 1 ]
then
  # \$ で$の特別な意味をエスケープし、文字列そのものを表示する。
  #echo "\$# => $#; $1"
  extname=$1
else
  # 代入の時には $ はつけない。
  # コマンドの出力を変数に代入可能である。
  # $() でコマンドをくくる。
  # `` バッククオートでくくる。の二通り。
  extname=$(date '+%Y%m%d-%H%M')
fi

# 変数内容の参照時は$をつける。
#echo $extname

# 変数の内容が スペースを含む可能性があるのでダブルクオートでくくる。
dest=".bashrc.$extname"

# コマンドの先頭に\ をつけると aliasを無効化できる。
\cp .bashrc $dest

if [ -e $dest ]
then
  echo "Complete! $dest" >&2
  # for ループ. ここでは ls の出力の文字列についてループ
  for file in `ls .bashrc.*`
  do
    echo "History $file"
  done
  exit 0
else
  exit 1
fi
```
