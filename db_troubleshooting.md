如果想要知道是否db層效能問題：
 
## 看看io wait time
如果 db 效能卡在 io，你應該看到 io wait time升起來的

## 看看 io throughput(disk 和 network 都要看)
如果你在 production 看到 io throughput graph 出現一個很高「平原」不再上去，那麼你的 db 有可能卡在 io

## 看看 CPU usage
如果 cpu 到達 100%，這可能是：
A) contention（今天這可能性很高，因為 CPU 效能過剩）
B) 真的 CPU 效能不足

## 看看 open connection 數字
如果你的 max_connection 開太小，有機會明明 db 還有 resources，但是外面進不來的
（註：open connection 太高絕對不是好事！）

## 看看有沒有 transaction 打開很久，但就是沒有 committed / rollback
留心，別跟 connection pool 的 idle connection 這 2 個不同的東西搞混亂
有用 connection pool 下, 有 idle connection 是很正常的
不正常的, 是很長時間沒結束的 tx

## Conclusion
很多時 db 效能問題，最終 root cause 都是 application 層亂來引起的。
一般來說，在沒看清楚 application 的 source code 寫怎樣前。
輕易改動 db 任何 performance 有關的設定是很危險的

## References
- https://www.facebook.com/groups/616369245163622
