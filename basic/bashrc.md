# bashrcの設定

## historyを100000まで増やす。 異なるターミナルの履歴も1つのファイルに記憶する。

```
# increse the number of history.
export HISTSIZE=100000
export HISTFILESIZE=100000
export PROMPT_COMMAND="history -a; history -c; history -r; $PROMPT_COMMAND"
shopt -u histappend
```

## Ctlr+C を押した時に^C が表示される場合、^Cを消す方法

```
[ -t 0 ] && stty -echoctl
```

