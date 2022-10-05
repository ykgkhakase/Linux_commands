# 計算機の負荷を表す指標、Load Averageの入手

uptime コマンドで入手可能。最後の数字3つがそれぞれ、直近1,5,15分間の平均値。

```bash
$ uptime
 10:55:18 up 110 days, 32 min,  3 users,  load average: 8.19, 8.10, 8.09
```

## 負荷の値だけを表示

```bash
$ uptime | cut -d ":"  -f 4
 8.07, 8.08, 8.08
```

## 直近 1分間の値を入手

```
$ uptime | cut -d ":"  -f 4 | cut -d , -f 1
 8.06
```

## 直近1分間の値が10以下だったらokと表示する。

```bash
[ $(echo "$(uptime | cut -d ":"  -f 4 | cut -d , -f 1) < 10" | bc -l) -gt 0 ] && echo ok
```
