# Git-Tutorial

This is a tutorial of git.

### Git Basic Command

使用git与远程仓库建立联系并改进提交的一系列顺序命令：

```bash
# 1-1 克隆/下拉远程项目
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

# 3 拉取远程项目更新、改进后提交。 正确节奏：pull → merge → push。
git pull origin <branch-name>
git fetch origin <branch-name>
git merge origin/<branch-name>
git add <file-name> [<file-name2>]  |  git add .
git commit -m 'commit message'
git push -u origin <branch-name>  | git push origin <branch-name>  | git push
```



### Git Command List

**git 常用命令列表：**

注意：命令中"<>"表示必填项，"[]"表示可选项。

<table>
    <tr>
        <th align="center" width="10">序号</th>
        <th align="center">命令类型</th>
        <th>具体命令</th>
        <th>释义</th>
        <th>备注</th>
    </tr>
    <tr>
        <td align="center">0</td>
        <td>git --version</td>
        <td>——</td>
        <td>查看当前git版本</td>
        <td>——</td>
    </tr>
    <tr>
        <td align="center" rowspan="2">1</td>
        <td rowspan="2">git config</td>
        <td>git config --list</td>
        <td>查看所有配置信息（包含全局+仓库+系统）</td>
        <td>1. 查看指定配置项：<strong>git config &lt;parameter-name&gt;</strong>，例如：git config user.name。<br />2. 区分层级查看配置项：git config [--global/--system/--local] --list，例如查看全局配置项：git config --global --list，其他“system”表示需要管理员权限的系统配置项，“local”表示当前默认仓库配置。</td>
    </tr>
    <tr>
        <td>git config [--global/--system/--local] &lt;parameter-name&gt; &lt;parameter-value&gt;</td>
        <td>设置配置项信息，可省略默认的local仓库级别</td>
        <td>1. 设置配置项信息示例：git config --global user.name "你的用户名"。<br />2. 删除配置项信息：<strong>git config [--global/--system/--local] --unset &lt;parameter-name&gt;</strong>。<br />3. 手动修改编辑配置文件：git config [--global/--system/--local] --edit。<br />4. 优先级：<strong>仓库级（local） &gt; 全局级（global） &gt; 系统级（system）</strong>，即同一配置项，仓库级会覆盖全局 / 系统级。</td>
    </tr>
    <tr>
        <td align="center">2</td>
        <td>git clone</td>
        <td>git clone &lt;project-url&gt;</td>
        <td>将远程仓库克隆到本地</td>
        <td>——</td>
    </tr>
    <tr>
        <td align="center">3</td>
        <td>git init</td>
        <td>git init [&lt;git-name/git-path&gt;]</td>
        <td>在本地创建并初始化一个新的空Git仓库</td>
        <td>1. 直接执行git init：在当前目录初始化仓库。<br />2. 执行git init my-project：创建名为my-project的目录并在其中初始化仓库。<br />3. 初始化后会生成隐藏的 .git 目录，包含仓库的所有配置和版本信息。</td>
    </tr>
    <tr>
        <td align="center" rowspan="5">4</td>
        <td rowspan="5">git remote</td>
        <td>git remote add origin &lt;project-url&gt;</td>
        <td>为本地仓库关联一个远程仓库，并命名为origin</td>
        <td>1. origin是远程仓库的默认别名。<br />2. 为本地仓库关联自定义别名的远程仓库，采用git remote add &lt;remote-alias&gt; &lt;project-url&gt;，如git remote add myrepo &lt;url&gt;，且可同时关联多个远程仓库（如origin、github）。<br />3. 关联后才能通过origin操作该远程仓库（如git push origin main）。</td>
    </tr>
    <tr>
        <td>git remote -v</td>
        <td>查看本地仓库已关联的所有远程仓库信息（包含fetch/push地址）</td>
        <td>“-v”是“--verbose”的简写，输出结果会显示远程仓库别名和对应的URL。</td>
    </tr>
    <tr>
        <td>git remote remove &lt;remote-name&gt;</td>
        <td>移除本地仓库与指定远程仓库的关联</td>
        <td>示例：git remote remove origin，仅删除本地关联，不影响远程仓库本身。</td>
    </tr>
    <tr>
        <td>git remote rename &lt;old-name&gt; &lt;new-name&gt;</td>
        <td>重命名已关联的远程仓库别名</td>
        <td>示例：git remote rename origin my-github，将默认的origin重命名为my-github。</td>
    </tr>
    <tr>
        <td>git remote set-url &lt;remote-alias&gt; &lt;new-url&gt;</td>
        <td>修改已关联远程仓库的URL地址</td>
        <td>1. 示例：git remote set-url origin git@github.com:xxx/xxx.git；<br />2. 适用场景：远程仓库地址变更、HTTPS切换为SSH协议等。</td>
    </tr>
    <tr>
        <td align="center" rowspan="2">5</td>
        <td rowspan="2">git switch</td>
        <td>git switch -c &lt;new-branch-name&gt;</td>
        <td>创建并切换一个新分支</td>
        <td>与git旧版本命令“<strong>git checkout -b &lt;new-branch-name&gt;</strong>”效果相同。</td>
    </tr>
    <tr>
        <td>git switch &lt;branch-name&gt;</td>
        <td>切换到一个分支</td>
        <td>与git旧版本命令“<strong>git checkout &lt;branch-name&gt;</strong>”效果相同。</td>
    </tr>
    <tr>
        <td align="center">6</td>
        <td>git add</td>
        <td>git add &lt;file-name&gt; [&lt;file-name2&gt;]</td>
        <td>添加文件到暂存区</td>
        <td>其中参数中"."(所有)、"*"(通配)、"?"(单字符匹配)等都有相应含义，示例：“<strong>git add .</strong>”、“<strong>git add *.md</strong>”、"<strong>git add m?.txt</strong>"。</td>
    </tr>
    <tr>
        <td align="center" rowspan="2">7</td>
        <td rowspan="2">git commit</td>
        <td>git commit -m 'commit message'</td>
        <td>将暂存区更改提交到本地仓库，并添加提交信息</td>
        <td>1. 提交并添加包含临时标记的提交信息，git commit -m "WIP: 正在开发的**功能"，其中WIP（Work In Progress）是通用约定，标识“功能未完成”。<br />2. 提交信息支持双引号/单引号，特殊字符需转义（如\*\*）。<br />3. 建议提交信息清晰：类型(模块): 具体描述（如feat(login): 新增验证码登录）。</td>
    </tr>
    <tr>
        <td>git commit -a -m 'commit message'</td>
        <td>自动将已跟踪的修改文件加入暂存区，并直接提交（跳过git add）</td>
        <td>1. “-a”等价于对所有已跟踪文件执行git add。<br />2. 不处理新增的未跟踪文件（仍需手动git add）。<br />3. 示例：git commit -a -m '修复用户登录验证逻辑'。</td>
    </tr>
    <tr>
        <td align="center" rowspan="2">8</td>
        <td rowspan="2">git pull</td>
        <td>git pull origin &lt;branch-name&gt;</td>
        <td>拉取远程最新更改并合并到当前本地分支</td>
        <td>1. 可简化为git pull拉取跟踪的分支。<br />2. 本质是<strong>git fetch + git merge</strong>的组合命令。</td>
    </tr>
    <tr>
        <td>git pull --no-rebase [origin main]</td>
        <td>拉取远程分支并以merge方式合并（禁用rebase模式）</td>
        <td>1. --no-rebase：强制使用merge（默认行为，可显式指定）。<br />2. 对比git pull --rebase：rebase是“变基”合并，无多余合并提交。<br />3. 示例：git pull --no-rebase origin main（拉取远程main并merge）。</td>
    </tr>
    <tr>
        <td align="center">9</td>
        <td>git push</td>
        <td>git push origin &lt;branch-name&gt;</td>
        <td>将本地更改推送到远程仓库对应分支</td>
        <td>1. 可简化为git push推送到跟踪分支。<br />2. 首次推送到远程并建立关联“<strong>git push -u origin &lt;branch-name&gt;</strong> ”。</td>
    </tr>
    <tr>
        <td align="center">10</td>
        <td>git fetch</td>
        <td>git fetch &lt;remote-name&gt; &lt;branch-name&gt;</td>
        <td>拉取远程仓库分支更新到本地（仅下载，不合并）</td>
        <td>0. 默认使用git fetch origin <branch-name>。<br />1. 执行git fetch：拉取所有远程分支的最新更改。<br />2. 与git pull的区别：fetch只下载不合并，pull是下载+合并，fetch更安全，可先查看更改再决定是否合并。<br />3. 查看fetch的更改：<strong>git diff &lt;local-branch&gt; origin/&lt;remote-branch&gt;</strong>。</td>
    </tr>
    <tr>
        <td align="center" rowspan="2">11</td>
        <td rowspan="2">git merge</td>
        <td>git merge &lt;target-feature-name&gt;</td>
        <td>将目标分支自动合并到当前所在分支</td>
        <td>合并feature/login分支到当前在main分支的命令示例：git merge feature/login 或 git merge origin/branch-name。</td>
    </tr>
    <tr>
        <td>git merge --abort</td>
        <td>中止/放弃合并，恢复到合并前的干净状态</td>
        <td>——</td>
    </tr>
    <tr>
        <td align="center" rowspan="4">12</td>
        <td rowspan="4">git branch</td>
        <td>——</td>
        <td>列出本地所有分支（当前分支前带*标记）</td>
        <td>——</td>
    </tr>
    <tr>
        <td>git branch [-v/-vv]</td>
        <td>列出本地所有分支并显示额外信息</td>
        <td>1. <strong>git branch -v</strong>：列出本地分支并显示每个分支最后一次提交的信息（版本号+提交说明）。<br />2. <strong>git branch -vv</strong>：额外显示分支关联的远程分支信息。</td>
    </tr>
    <tr>
        <td>git branch -r</td>
        <td>列出远程仓库的所有分支</td>
        <td>1. <strong>git branch -a</strong>：列出本地+远程所有分支。<br />2. 远程分支名称格式通常为origin/&lt;branch-name&gt;。</td>
    </tr>
    <tr>
        <td>git branch [-d/-D] &lt;branch-name&gt;</td>
        <td>删除本地指定分支（-d需分支已合并，-D强制删除）</td>
        <td>1. 删除远程分支：<strong>git push origin --delete &lt;branch-name&gt;</strong>（示例：git push origin --delete new-feature）。<br />2. 删除前建议先切换到其他分支（如main）。</td>
    </tr>
    <tr>
        <td align="center">13</td>
        <td>git status</td>
        <td>——</td>
        <td>查看当前工作区和暂存区的状态</td>
        <td>1. 显示已修改但未暂存、已暂存但未提交的文件。<br />2. <strong>git status -s</strong>：精简输出（短格式），仅显示文件状态缩写（如M=修改、A=新增、??=未跟踪）。<br />3. 帮助判断是否需要git add/git commit操作。</td>
    </tr>
    <tr>
        <td align="center" rowspan="3">14</td>
        <td rowspan="3">git diff</td>
        <td>——</td>
        <td>对比工作区与暂存区文件的差异</td>
        <td>仅显示未执行git add的文件修改内容。</td>
    </tr>
    <tr>
        <td>git diff [--staged/--cached]</td>
        <td>对比暂存区与本地仓库最新提交的差异</td>
        <td>查看已执行git add但未git commit的文件修改内容。</td>
    </tr>
    <tr>
        <td>git diff &lt;branch1&gt; &lt;branch2&gt;</td>
        <td>对比两个分支之间的文件差异</td>
        <td>1. 示例：git diff main feature/login，查看main和feature/login分支的差异。<br />2. 查看fetch操作本地分支与远程分支间的更改：git diff &lt;local-branch&gt; origin/&lt;remote-branch&gt;。</td>
    </tr>
    <tr>
        <td align="center" rowspan="4">15</td>
        <td rowspan="4">git stash</td>
        <td>——</td>
        <td>暂存当前工作区/暂存区的未提交更改，恢复干净工作区</td>
        <td>1. 可选备注：git stash "临时修改备注"。<br />2. 暂存未跟踪文件需加<strong>-u</strong>参数。</td>
    </tr>
    <tr>
        <td>git stash pop</td>
        <td>恢复最近一次stash的更改，并删除该临时快照</td>
        <td>1. 恢复指定快照：<strong>git stash pop stash@{0}</strong>（stash@{0}为最近一次）。<br />2. 仅恢复不删除可用：<strong>git stash apply</strong>。</td>
    </tr>
    <tr>
        <td>git stash list</td>
        <td>列出本地所有已保存的stash临时快照</td>
        <td>1. 输出示例：stash@{0}: On main: 临时修改备注。<br />2. 快照编号（如stash@{0}）用于定位指定快照，配合pop/apply/drop使用。<br />3. 执行<strong>git stash list -v</strong>可查看快照详细修改记录。</td>
    </tr>
    <tr>
        <td>git stash drop</td>
        <td>删除指定/最近一次stash临时快照（不恢复更改）</td>
        <td>1. 删除最近一次：git stash drop（等价git stash drop stash@{0}）。<br />2. 删除指定快照：<strong>git stash drop stash@{1}</strong>。<br />3. 清空所有快照：<strong>git stash clear</strong>（谨慎使用，不可恢复）。</td>
    </tr>
    <tr>
        <td align="center" rowspan="4">16</td>
        <td rowspan="4">git log</td>
        <td>——</td>
        <td>查看本地仓库当前分支的完整提交历史（默认按时间倒序）</td>
        <td>1. 默认输出：提交哈希、作者、时间、提交信息。<br />2. 常用翻页：按<strong>空格</strong>下一页，<strong>q</strong>退出查看。<br />3. 限制显示条数：<strong>git log -5</strong>（仅显示最近5条提交）。</td>
    </tr>
    <tr>
        <td>git log --oneline --graph --decorate</td>
        <td>以精简图形化格式展示提交历史（分支走向+提交信息+标签）</td>
        <td>1. --oneline：单行显示（提交哈希前7位+信息）。<br />2. --graph：绘制分支合并的ASCII图形。<br />3. --decorate：显示提交关联的分支/标签信息。</td>
    </tr>
    <tr>
        <td>git log main..origin/main</td>
        <td>查看本地main分支与远程origin/main分支的提交差异</td>
        <td>1. 输出：仅显示远程有但本地没有的提交。<br />2. 反向对比：<strong>git log origin/main..main</strong>（本地有但远程没有）。<br />3. 需先执行git fetch拉取远程最新提交。</td>
    </tr>
    <tr>
        <td>git log --follow &lt;file-name&gt;</td>
        <td>跟踪指定文件的所有提交历史（包含重命名/移动记录）</td>
        <td>1. 区别于普通git log &lt;file-name&gt;：普通方式会中断重命名后的记录，--follow可追踪完整历史。<br />3. 配合--oneline使用更精简：<strong>git log --oneline --follow demo.txt</strong>。</td>
    </tr>
    <tr>
        <td align="center" rowspan="4">17</td>
        <td rowspan="4">git reset</td>
        <td>git reset HEAD &lt;file-name&gt; / .</td>
        <td>将指定文件/所有文件从暂存区撤回至工作区（取消git add）</td>
        <td>1. git reset HEAD demo.txt：撤回demo.txt。<br />2. git reset HEAD .：撤回所有暂存区文件。<br />3. 仅撤回暂存区，工作区修改保留。</td>
    </tr>
    <tr>
        <td>git reset --hard HEAD~1</td>
        <td>硬重置到上一个提交版本，清空工作区+暂存区修改</td>
        <td>1. HEAD~1：上一个提交（HEAD~2是上上个）。<br />2. 危险操作：未提交的修改会被永久删除。<br />3. 谨慎使用，建议先git stash暂存修改。</td>
    </tr>
    <tr>
        <td>git reset --hard HEAD@{1}</td>
        <td>硬重置到操作历史（reflog日志）的上一个HEAD状态</td>
        <td>1. HEAD@{1}：通过git reflog查看的历史HEAD记录。<br />2. 适用场景：恢复误操作的reset/merge/rebase。<br />3. 需先执行git reflog获取历史记录。</td>
    </tr>
    <tr>
        <td>git reset [--soft] HEAD~1</td>
        <td>软重置到上一个提交版本，保留工作区+暂存区修改</td>
        <td>1. --soft：仅撤销提交，修改保留在暂存区.<br />2. 无参数（默认--mixed）：撤销提交+撤回暂存区，修改保留在工作区。<br />3. 适用场景：合并多个提交（修改上一次提交）。</td>
    </tr>
    <tr>
        <td align="center" rowspan="2">18</td>
        <td rowspan="2">git restore</td>
        <td>git restore --staged .</td>
        <td>将所有文件从暂存区撤回至工作区（等价于git reset HEAD .）</td>
        <td>1. --staged：指定操作暂存区。<br />2. Git新版本增加命令，替代旧的git reset HEAD。<br />3. 仅撤回暂存区，工作区修改不变。</td>
    </tr>
    <tr>
        <td>git restore demo/poem.txt</td>
        <td>放弃工作区中指定文件的所有修改，恢复到最近一次提交状态</td>
        <td>1. 危险操作：未提交的修改会被覆盖。<br />2. 恢复所有文件：<strong>git restore .</strong>。<br />3. 区别：restore专注恢复文件，reset专注重置提交。</td>
    </tr>
    <tr>
        <td align="center">19</td>
        <td>git rebase</td>
        <td>git rebase -i &lt;commit-hash&gt;</td>
        <td>交互式变基，编辑指定提交（commit-code）之后的所有提交记录</td>
        <td>1. -i（--interactive）：进入交互式编辑界面。<br />2. 示例：git rebase -i abc1234，其中abc1234表示提交的哈希前缀（也可用HEAD~3指定前3个提交）。<br />3. 常用操作：pick（保留）、reword（改信息）、squash（合并）、drop（删除）。<br />4. 用于整理提交记录（如合并多次临时提交）。</td>
    </tr>
    <tr>
        <td align="center">20</td>
        <td>git reflog</td>
        <td>——</td>
        <td>查看本地仓库的HEAD指针历史记录（所有操作轨迹）</td>
        <td>1. 记录包括：提交、reset、merge、rebase、checkout等操作。<br />2. 输出示例：abc1234 HEAD@{0}: reset: moving to HEAD~1。<br />3. 核心价值：恢复误操作（如误reset/删除分支），Git的“后悔药”。</td>
    </tr>
    <tr>
        <td align="center">21</td>
        <td>git gc</td>
        <td>——</td>
        <td>垃圾回收，清理仓库中无用的对象（缓存、未引用的提交等）</td>
        <td>1. gc（garbage collection）：自动优化仓库存储。<br />2. 通常Git会自动触发，无需手动执行。<br />3. 手动执行场景：仓库体积过大、操作频繁后清理。<br />4. 安全操作：仅清理无用数据，不影响有效提交。</td>
    </tr>
    <tr>
        <td align="center">22</td>
        <td>git revert</td>
        <td>git revert &lt;commit-hash&gt;</td>
        <td>创建新提交，撤销指定提交（commit-hash）的所有修改</td>
        <td>1. 区别于git reset：revert是“反向提交”，保留历史记录；reset是“删除提交”，修改历史。<br />2. 适用场景：撤销已推送到远程的提交（不破坏公共历史）。<br />3. 示例：git revert abc1234，撤销abc1234提交的修改。<br />4. 若有冲突，需解决后执行git revert --continue。</td>
    </tr>
    <tr>
        <td align="center">23</td>
        <td>gitk</td>
        <td>——</td>
        <td>内建的图形化 git</td>
        <td>——</td>
    </tr>
    <tr>
        <td align="center">24</td>
        <td>git rm</td>
        <td>git rm [--cached] &lt;file-name&gt;</td>
        <td>从Git版本控制中删除文件（可选保留本地文件）</td>
        <td>1. 直接执行git rm demo.txt：删除版本库+本地文件（物理删除）。<br />2. 加--cached：<strong>git rm --cached demo.txt</strong>：仅删除版本库中的记录，本地文件保留。<br />3. 适用场景：--cached用于取消文件的Git跟踪（如误提交的配置文件）。</td>
    </tr>
    <tr>
        <td align="center">25</td>
        <td>git mv</td>
        <td>git mv &lt;file-original&gt; &lt;file-renamed&gt;</td>
        <td>重命名/移动Git跟踪的文件，并将修改纳入版本控制</td>
        <td>1. 重命名示例：git mv old.txt new.txt（等价于git add new.txt + git rm old.txt）。<br />2. 移动示例：git mv demo.txt src/demo.txt（将文件移动到src目录）。<br />3. 若目标文件已存在，需加<strong>-f</strong>强制覆盖：git mv -f old.txt new.txt。</td>
    </tr>
    <tr>
        <td align="center">26</td>
        <td>git show</td>
        <td>git show [&lt;commit-hash&gt;/&lt;branch-name&gt;/&lt;tag-name&gt;]</td>
        <td>查看最新提交/指定提交/分支/标签的详细信息（含修改内容、作者、时间等）</td>
        <td>1. 无参数执行git show：查看最新一次提交（HEAD）的详细信息。<br />2. 查看指定提交：git show abc1234（abc1234为提交哈希前7位）。<br />3. 查看分支最新提交：git show dev（等价于git show dev@{0}）。<br />4. 查看标签对应提交：git show v1.0.0（显示标签信息+提交详情）。<br />5. 仅看文件修改：<strong>git show abc1234 -- demo.txt</strong>（只显示该提交中demo.txt的修改内容）。</td>
    </tr>
</table>



---

### 一、Git环境配置

首次使用 Git 时配置身份：

```bash
git config --global user.name "你的名字"
git config --global user.email "your.email@example.com"
```

推荐全局配置环境：

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

### 二、分支建立跟踪关系的原则

Git 中分支跟踪关系（upstream）的核心原则是 **“一对一关联”**，即：

1. **一个本地分支只能跟踪一个远程分支**（通常是同一仓库的同名分支，也可手动指定不同名分支）。
2. 跟踪关系的主要作用是 **简化 `git pull` 和 `git push` 命令**，默认操作关联的远程分支，无需每次指定远程仓库和分支名。
3. 跟踪关系通常遵循 **“同名对应”** 习惯（如本地 `main` 跟踪远程 `origin/main`），但可通过命令自定义（如本地 `dev` 跟踪 `origin/develop`）。

### 三、跟踪关系与 `git pull`/`git push` 的作用对象

当本地分支已建立跟踪关系（例如本地 `feature` 跟踪 `origin/feature`），之后执行 `git pull <另一个远程仓库> <另一个分支>`（如 `git pull github dev`）时：

- 这只是 **临时拉取指定远程仓库的指定分支到当前本地分支**，**不会改变原有的跟踪关系**。

因此：

1. 执行 `git pull`（不带参数）时，仍会默认拉取 **原跟踪的远程分支**（如 `origin/feature`）的更新。
2. 执行 `git push`（不带参数）时，仍会默认推送到 **原跟踪的远程分支**（如 `origin/feature`）。

### 四、举例说明

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

### 五、Git相关介绍

Git 的工作流程分为四个主要部分：

1.  工作区 (Working Directory) —— 电脑里能看到的目录；实际修改文件的地方（ 你的书桌）
   - 版本库 (Repository) ：工作区有一个隐藏目录 .git，这个不算工作区，而是 Git 的版本库。
2.  暂存区 (Staging Area) —— stage 或 index 区域，一般存放在 .git 目录下的 index 文件中，故暂存区有时也叫作索引；将写完的作业放进篮子里准备打包（你的待邮寄篮子）
3.  本地仓库 (Local Repository) —— 将篮子里东西打包并贴上标签（提交信息）后锁进自己的保险箱（你的个人保险箱）
4.  远程仓库 (Remote Repository) —— 把保险箱内代码通过网络发送给远程服务器（老师的收件箱，如 GitHub/GitLab）

工作区、暂存区和版本库之间的关系：**工作区 —> 暂存区 —> 版本库 —> 远程仓库 —> 本地版本库**

Git 的文件状态转换流程：未跟踪（Untracked）、已跟踪（Tracked）、已修改（Modified）、已暂存（Staged）、已提交（Committed）

### 六、总结

- 跟踪关系是本地分支与**一个远程分支**的固定关联，临时拉取其他远程内容不会改变它。
- 无参数的 `git pull`/`git push` 始终以**当前分支已建立的跟踪关系**为目标，与临时拉取的其他远程仓库无关。
- 若需改变默认操作的远程 / 分支，需重新通过 `git branch --set-upstream-to` 修改跟踪关系。




---

PS：

1. git - 简明指南：https://rogerdudler.github.io/git-guide/index.zh.html
2. git reference：https://git-scm.com/docs
3. git cheat sheet：https://www.runoob.com/manual/github-git-cheat-sheet.pdf
4. **git tutorial of runoob** (git基本操作命令) ：https://www.runoob.com/git/git-basic-operations.html
