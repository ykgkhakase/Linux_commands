# GNU Screen とは

(:link:)[https://ja.wikipedia.org/wiki/GNU_Screen]

ssh で計算サーバーに接続した場合、ターミナルソフト(MobaXterm等）を閉じると例えば計算時間が長いジョブも同時に終了してしまう。
そこで screen 上で作業をすることで、計算を持続することができる。

またサーバー上での作業状態を保存できるので、例えばディレクトリ移動や環境変数等の再設定の手間を省けるので、研究の再開が容易になるメリットもある。


実は他にも方法があるがそれはここでは触れない。(例: nohup 等）

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

screenはデフォルトだと見栄えが良くないが、カスタマイズが可能である。
例えば下記の内容を .screenrc に書き込む。

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
で起動中の screen のリストを見てから -r でscreenの名前を指定する。

### デタッチ (detach)
screen を起動中に Ctrl+g d を入力

### 著者がよく使う最小限どのコマンド
※ 上のトリガーをCtrl+g として設定した場合。

- 新しいウインドを開く Ctrl+g c
- 以前のウインドに　移動する。 Ctrl+g p 
- 次ののウインドに　移動する。 Ctrl+g n
- 指定したウインド移動する。例えば一番のウインド Ctrl+g 1
 
