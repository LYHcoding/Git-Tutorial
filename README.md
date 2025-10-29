
# 🧭 Git 自救训练仓库（教学版）

> 目标：在多人协作中，学会 **本地自救**（不慌、会看现场、能恢复）。

## ⚙️ 实验准备

### 1) 安装
- Git: https://git-scm.com/downloads 或者 https://repo.ntic-spm.net/repository/file-repo/Git-2.51.0.2-64-bit.exe
- VSCode: https://code.visualstudio.com/ 或者 https://repo.ntic-spm.net/repository/file-repo/VSCodeUserSetup-x64-1.105.1.exe

### 2) 首次使用 Git 时配置身份
```bash
git config --global user.name "你的名字"
git config --global user.email "your.email@example.com"
```

### 3) 统一课堂环境（推荐全局配置）
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
git config --global push.autoSetupRemote true
git config --global http."https://gitlab.spm.org:50493/".sslVerify false

```

### 4) 克隆本仓库
```bash
git clone https://gitlab.spm.org:50493/sandbox/gitlab-sandbox-training.git
cd gitlab-sandbox-training
```

### 目录结构
```
demo/   # 实验用文件（冲突/对比/演示）
labs/   # 各讲实验讲义（Markdown）
```
