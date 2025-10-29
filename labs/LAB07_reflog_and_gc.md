
# LAB07：reflog 与 Git 垃圾回收（gc）

**目标**：知道“后悔药”在哪；理解 reflog 保留策略与 `git gc` 的清理。

## 步骤：模拟误操作并找回
```bash
# 先确保有多次提交
git switch feature/<your-name> 
echo now >> demo/history.txt
git add . && git commit -m "temp change"

# 故意回退两步
git reset --hard HEAD~2

# 用 reflog 找回
git reflog
# 观察类似：HEAD@{1} 或具体 commit-id
git reset --hard HEAD@{1}
```

## 保留策略（默认）
- 可达对象：约保留 90 天（`gc.reflogExpire`）
- 不可达对象：约保留 30 天（`gc.reflogExpireUnreachable`）

可自定义：
```bash
git config --global gc.reflogExpire "180 days"
git config --global gc.reflogExpireUnreachable "90 days"
```

## 触发清理
```bash
git gc
```
> 提醒：gc 会清理旧对象；**重要历史要打 tag/branch**，别只靠 reflog。

## 验收
- 能通过 `reflog` 找回误删历史；
- 理解 reflog 是“本地时光机日志”，有保留期。

## 小结
- 删不掉的，其实都在（有时限）；
- 要长期保留 → 用 tag/branch。
