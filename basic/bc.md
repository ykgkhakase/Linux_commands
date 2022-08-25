# bc とは
bcとは簡単な電卓のようなコマンドである。

## bcの起動と終了

```
$ bc
bc 1.07.1
Copyright 1991-1994, 1997, 1998, 2000, 2004, 2006, 2008, 2012-2017 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'.
quit
```

## bc で足し算

1+2+3 = 6 を実行する。
なお起動時に--quietをつけると起動メッセージがなくなる。

```
$ bc --quiet
1+2+3
6
```

## bc でかけ算
```
$ bc --quiet
2*3
6
4*5/10
2
quit
```

## 小数点以下も表示する
scale=3 などの指定で指定した桁数を表示できる。

```
$ bc --quiet
10/3
3
scale=3
10/3
3.333
quit
```

## 冪乗など
^ を使うと 二乗などが可能

```
$ bc --quiet
2*2
4
2*2*2
8
2^3
8
2^4
16
2^62
4611686018427387904
2^32
4294967296
quit
```

