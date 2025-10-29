
# LAB05：越改越乱，想回到昨天那样（restore / reset）

**目标**：分清“未提交”与“已提交”的还原方法；建立“我能回去”的信心。

## 场景 A：未提交的改动太乱，我全回滚都不要了 **这个是没有后悔药的！！！！**
修改poem.txt
```bash
git status
git switch feature/<your-name>
git pull
git status
#修改 demo/poem.txt
git status
git restore demo/poem.txt #这个没有git后悔药，要找回看看IDE里还有没有历史　！！！

```

## 场景 B：已经add，还没有commit
修改poem.txt
```bash
git status
#修改 demo/poem.txt
git add demo/poem.txt
git status
git restore --stage demo/poem.txt　＃不会丢，不要怕
```


## 场景 C：已经提交了几次，也想回到昨天 (已经push的不能这样做！)
```bash
git switch -c backup/before-reset       # 先备份一条分支
git log --oneline
git reset --hard <commit-id>            # 回到目标提交（昨天）
```

## 场景 D：后悔药呢？？？（预告：第七讲细讲）


## 验收
- A：`git diff` 无输出；
- B：`git log` 指向目标提交；


## 小结
- `restore` 只动工作区；`reset --hard` 回到指定版本；
- 不确定时，**先备份分支**再动手。
