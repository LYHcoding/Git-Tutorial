# Git-Tutorial
This is a tutorial of git.

### Git Basic Command
使用git与远程仓库建立联系并改进提交的一系列顺序命令：
```bash
# 1-1 下拉远程项目
git clone <project-url> 
cd <project-name>
# 1-2 新建本地项目
cd <project-name>
git init
git remote add origin <project-url>

# 2 查看当前git信息
git remote -v
git branch -v
git switch -c <branch-name>  |  git switch <branch-name>
git status
git diff

# 3 拉取远程项目更新、改进后提交
git pull origin <branch-name>
git fetch origin <branch-name>
git merge origin/<branch-name>
git add <file-name> [<file-name2>]  |  git add .
git commit -m 'commit message'
git push -u origin <branch-name>  | git push origin <branch-name>  | git push
```

### Git Command List

git 常用命令列表：

| 序号 | 命令 | 释义 | 备注 |
| ---- | ---- | ---- | ---- |
|0|git --version|查看当前git版本||
|1|git config --list|查看配置信息|使用“**git config --global \<parameter-name> \<parameter-value>**”命令进行编辑配置信息|
|2|git clone <project-url>|从远程仓库克隆项目到本地||
|3|git switch -c <branch-name>|创建并切换一个新分支|与git旧版本命令“**git checkout -b \<branch-name>**”效果相同|
|4|git add <file-name> [<file-name2>]|添加文件到暂存区|其中参数中"."(所有)、"*"(通配)、"?"(单字符匹配)等都有相应含义，示例：“**git add .**”|
|5|git commit -m 'commit message'|将暂存区更改提交到本地仓库||
|6|git pull origin <branch-name>|拉取远程最新更改|可简化为“**git pull**”拉取跟踪的分支|
|7|git push origin <branch-name>|将本地更改推送到远程仓库|1.可简化为“**git push**”推送到跟踪分支<br />2.首次推送到远程并建立关联“**git push -u origin \<branch-name>** ”|
|8||||
|9||||



git init

git branch  |  git branch -v  |  git branch -r 

git status

git diff

git remote -v

git remote set-url origin git@github.com:LYHcoding/Git-Tutorial.git

git remote add github git@github.com:LYHcoding/Git-Tutorial.git

git commit -a -m 'commit message'

git log --oneline --graph --decorate

git log main..origin/main  # 对比本地 main 和远程 origin/main 的差异

git commit -m "WIP: 正在开发的**功能"

git pull --no-rebase  |  git pull --no-rebase origin main

git reset HEAD <文件名>  |  git reset HEAD .  |  git reset --hard HEAD~1

git reset --soft HEAD~1   |  git reset HEAD~1

git restore --staged .

git revert <commit-hash>

git fetch <远程仓库> <远程分支>   # 拉取远程更新到本地

git merge origin/<远程分支>       # 自动合并到当前本地分支

git branch -d <分支名>  |  git branch -D <分支名>

git stash

git stash pop



----



### 一、分支建立跟踪关系的原则

Git 中分支跟踪关系（upstream）的核心原则是 **“一对一关联”**，即：

1. **一个本地分支只能跟踪一个远程分支**（通常是同一仓库的同名分支，也可手动指定不同名分支）。
2. 跟踪关系的主要作用是 **简化 `git pull` 和 `git push` 命令**，默认操作关联的远程分支，无需每次指定远程仓库和分支名。
3. 跟踪关系通常遵循 **“同名对应”** 习惯（如本地 `main` 跟踪远程 `origin/main`），但可通过命令自定义（如本地 `dev` 跟踪 `origin/develop`）。

### 二、跟踪关系与 `git pull`/`git push` 的作用对象

当本地分支已建立跟踪关系（例如本地 `feature` 跟踪 `origin/feature`），之后执行 `git pull <另一个远程仓库> <另一个分支>`（如 `git pull github dev`）时：

- 这只是 **临时拉取指定远程仓库的指定分支到当前本地分支**，**不会改变原有的跟踪关系**。

因此：

1. 执行 `git pull`（不带参数）时，仍会默认拉取 **原跟踪的远程分支**（如 `origin/feature`）的更新。
2. 执行 `git push`（不带参数）时，仍会默认推送到 **原跟踪的远程分支**（如 `origin/feature`）。

### 举例说明

1. 本地分支 `test` 与 `origin/test` 建立跟踪关系：

   ```bash
   git push -u origin test  # 本地 test 跟踪 origin/test
   ```

   此时 `git pull` 等价于 `git pull origin test`，`git push` 等价于 `git push origin test`。

2. 临时拉取另一个远程仓库 `github` 的 `dev` 分支到本地 `test`：

   ```bash
   git pull github dev  # 仅本次拉取 github/dev，不改变跟踪关系
   ```

   之后执行 `git pull` 或 `git push`：

   - 仍默认操作原跟踪的 `origin/test`，而非 `github/dev`。

### 总结

- 跟踪关系是本地分支与**一个远程分支**的固定关联，临时拉取其他远程内容不会改变它。
- 无参数的 `git pull`/`git push` 始终以**当前分支已建立的跟踪关系**为目标，与临时拉取的其他远程仓库无关。
- 若需改变默认操作的远程 / 分支，需重新通过 `git branch --set-upstream-to` 修改跟踪关系。



---



### Git Experiment Example



