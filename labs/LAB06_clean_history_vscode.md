
# LAB06：历史太碎，想“整理一下”（VSCode 版交互式 rebase）

**目标**：把多次 WIP 合成干净历史；用`git log` 找起点。  
仅在 **未推送** 的分支上操作。

## 准备：先随便做 3 次提交
```bash
git switch feature/<your-name> 
echo "v1" > demo/history.txt
git add . && git commit -m "implement new feature"
echo "v2" >> demo/history.txt
git commit -am "add some code"
echo "v3" >> demo/history.txt
git commit -am "add new code"
```

## 配置 VSCode 为编辑器（课前可统一）
```bash
git config --global core.editor "code --wait"
```

## 用 log 找“起点”
```bash
git log --oneline --graph
# 找到“implement new feature” 之前 的 commit-id（例如 abc1234）
git switch -c backup/before-rebase      # 先备份
git status
git switch feature/<your-name>           # 回到原分支
git status
git rebase -i abc1234
```

VSCode 会打开一个文件，例如：
```
pick 4b817a8 # implement new feature
pick 7da16e9 # add some code
pick a2f8266 # add new code
```
把后两条改为 `squash` 或 `fixup`：
```
pick 4b817a8 # implement new feature
f 7da16e9 # add some code
f a2f8266 # add new code
```
保存退出，合并 commit message，完成。

## 验收
```bash
git log --oneline
```
只剩一条“干净提交”。

## 小结
- 看 log 找起点；
- rebase 会改历史，**未推送**时才用；
- 推送后要“干净”，合并时可用 squash。
