
# 🧭 Git 自救训练仓库

## ⚙️ 实验准备

### 1️⃣ 安装工具
- [Git 下载](https://git-scm.com/downloads)
- [VSCode 下载](https://code.visualstudio.com/)

### 2️⃣ 初次使用 Git 时配置身份
```bash
git config --global user.name "你的名字"
git config --global user.email "your.email@example.com"
```

### 3️⃣ 推荐全局配置（统一课堂环境）
```bash
git config --global core.editor "code --wait"
git config --global diff.tool vscode
git config --global difftool.vscode.cmd "code --wait --diff $LOCAL $REMOTE"
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd "code --wait --merge $BASE $LOCAL $REMOTE $MERGED"
git config --global mergetool.prompt false
git config --global mergetool.keepBackup false
git config --global merge.conflictStyle zdiff3
git config --global rerere.enabled true
```

### 4️⃣ 克隆仓库
```bash
git clone <repo-url>
cd gitlab-sandbox-training
```

### 5️⃣ 实验目录说明
```
demo/   # 实验用文件
labs/   # 实验讲义（Markdown）
```
