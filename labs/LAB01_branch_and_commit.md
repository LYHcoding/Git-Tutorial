
# LAB01：分支协作与第一次提交（不推远端）

**目标**：会创建分支、修改文件、提交快照；理解“commit 是本地时间点”。  
**不 push**，只在本地完成练习。

## 步骤
```bash
git status
git switch -c feature/<your-name>      # 新建并切到你的分支

echo "Hello Git from <your-name>" > demo/<your-name>.txt
git status
git diff

git add demo/<your-name>.txt
git diff
git commit -m "feat: add my first git file"

git log --oneline --graph --decorateq
```

## 验收
- `demo/<your-name>.txt` 出现；
- `git log` 能看到你的提交；
- 未执行 `git push`。

## 小结
- Git commit 只在本地；是“快照”。
- main 分支暂时不动。
