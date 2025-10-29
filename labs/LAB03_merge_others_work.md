
# LAB03：写到一半，要合别人的分支（不用 stash 的安全做法）

**目标**：功能半途需要吸收他人改动；学会“WIP 提交 + 备份分支 + 合并”。  
这讲我们**不合 main**，改为合 `feature/deathstar-blueprint` 分支。


## 学员步骤
```bash
git status
git switch feature/<your-name>                           # 回到你的工作分支
git log
# 随便修改一些内容
git status
git add . && git commit -m "WIP: save in-progress work"  # 1) 保存现场
git switch -c feature/<your-name>-merge-deathstar        # 2) 切换新工作分支
git fetch origin feature/deathstar-blueprint             # 3) 拉取指定分支
git merge origin/feature/deathstar-blueprint             # 4) 合并别人的改动


git push
```

## 验收
- 产生“Merge branch 'feature/deathstar-blueprint' into feature/<your-name>-merge-deathstar”记录；
- 文件包含双方合理改动；
- main 不变。

## 小结
- **不要乱用 stash**（容易忘记）；
- WIP 提交可追溯、可回滚、能“后悔药”。
