# 🧨 LAB04：合并冲突（VSCode 三路合并练习）

**目标**  
体验真实冲突：多人同时修改同一文件。  
学习用 `git mergetool` + VSCode 的可视化界面解决冲突。

---

## 🧩 步骤

### 1️⃣ 切到 group，准备实验
```bash
git status
git switch group/<groupname>
git pull
git log
```

### 2️⃣ 修改文件并提交（不要推送！）
所有人都修改同一个文件：
```
demo/conflict.txt
```
示例修改：
```
+ line-3: updated by <your-name>
```

保存后执行：
```bash
git add demo/conflict.txt
git commit -m "feat: local change in conflict.txt"
# 暂时不要 push
```



---

### 3️⃣ 所有组员
```bash
git pull --no-rebase
```

> 有的组员出现冲突提示：
```
CONFLICT (content): Merge conflict in demo/conflict.txt
Automatic merge failed; fix conflicts and then commit the result.
```

---

### 4️⃣ 查看状态并启动合并工具
```bash
git status
git mergetool
```

> VSCode 将打开合并界面：
> - 右上角点击 **⋯ → Show Base Center** 打开三路视图  
> - 选择 **Accept Current / Incoming / Both**  
> - 或直接在下方 **Result** 区编辑  
> - 保存并关闭文件

---

### 5️⃣ 完成合并并提交
```bash
git add demo/conflict.txt
git merge --continue
git push
```

---

## ✅ 验收
- push 成功；  
- `demo/conflict.txt` 最终修复；  
- `git log --oneline --graph` 能看到合并节点。  

---

## 🧠 提示
- 改乱了就退出：
  ```bash
  git merge --abort
  ```
- 想重来：
  ```bash
  git reset --hard <commit-id>
  git pull --no-rebase
  git mergetool
  ```
