
# LAB02：推不上去怎么办（用 pull + merge 自救）

**目标**：体验 non-fast-forward；学习“先同步，再合并”。  


## 学员步骤（命令行）
组长
```bash
git switch main
git switch -c group/<groupname>
git push #推个没有的分支
```

所有组员

```bash
git status
git switch main
git pull
git branch -r
git switch group/<groupname>
git log

git merge feature/<your-name>           # 合并你在 LAB01 的工作分支
git log --oneline --graph --decorate
# 等老师指令后，再执行下面的操作
git push                                # 如果推送失败执行下面步骤

git pull                                # 然后再push，失败了再pull，直到后续push成功
```

## 验收
- `git log --oneline --graph` 显示老师更新 + 你的合并提交；
- `git push` 成功，无冲突。

## 小结
- 遇到“推不上去”并不是坏事，是远端先更了；
- 正确节奏：**pull → merge → push**。
