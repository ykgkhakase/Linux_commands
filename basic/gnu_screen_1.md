# GNU Screen とは

## GNU screen の起動と終了


```
# 起動
$ screen 
```

```
# 終了
# 画面に [screen is terminating] と出るまで
$ exit 
を入力し続けるなど。
```

### .screenrc の設定例

インターネットにいろいろな設定が転がっているので参考にしてください。

```
vbell off
startup_message off
autodetach on
# Ctrl+A から Ctrl+G にトリガーを変更する。
# escape ^g^g
hardstatus alwayslastline '%{= Kk}%m/%d %02c:%s %H %L=%-w%45L>%{= g.}%n %t%{-}%+w %-17<%=%{= .y}(%l)'
scrollback 5000

defbce on
term xterm-256color

termcapinfo xterm "WS=\E[8;%d;%dt"
termcapinfo xterm "li#45:co#145"
```

.sceenrc は ホームディレクトリの下に作成する。
```
$ vi ~/.screenrc
```

### アタッチとデタッチ

#### アタッチ（attach)
デタッチされたscreen が1つの場合

```
$ screen -r 
```

2つ上ある場合は
```
$ screen -ls 
```
で起動中の screen のリストを見てから -r で指定する。

### デタッチ (detach)
screen を起動中に Ctrl+G d を入力


### 著者がよく使うコマンド
※ 上のトリガーをCtrl+g として設定した場合。

- 新しいウインドを開く Ctrl+g c
- 以前のウインドに　移動する。 Ctrl+g p 
- 次ののウインドに　移動する。 Ctrl+g n
- 指定したウインド移動する。例えば一番のウインド Ctrl+g 1
 



