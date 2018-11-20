# Git说明
---

### 一、专用名词
版本库：`.git文件夹`，里面包含两部分：暂存区和本地仓库；<br>

| 名词 | 解释 |
| :--- | :--- |
| Workspace | 工作区，本地电脑存放项目文件的地方 |
| Index/Stage | 暂存区，存在于`.git文件夹`，存放临时文件，用来准备一个提交，但可以不用把工作目录中所有的修改内容都包含进来。这样你可以创建一个高度聚焦的提交，尽管你本地修改很多内容。使用add命令之后，将工作区的改动文件添加到此处 |
| 本地仓库 | 存在于`.git文件夹`，是各个分支存储处，包括git自动创建的master分支，使用commit命令可以将暂存区中的文件添加到本地仓库中 |
| 远程仓库 | 存在于git服务器 |

![仓库之间的操作](https://github.com/gycold/GitAbout/blob/master/pictures/仓库之间的操作.png "仓库之间的操作")

### 二、关于4个区的常用操作命令
| 命令 | 作用 |
| :--- | :--- |
| `git add [file]或.` | 将改动从工作区提交到暂存区 |
| `git commit -m "提交说明"` | 将暂存区改动提交到本地仓库 |
| `git pull` | 拉取远程仓库改动至工作区 |
| `先git fetch`，然后`git merge` | 拉取远程仓库改动至本地仓库，然后合并工作区 |
| `git push origin master` | 一般使用简单写法```git push```：推送本地仓库改动至远程仓库 |

---

### 三、Git配置操作命令
git的配置文件为```.gitconfig```，它可以在用户主目录下（全局配置），也可以在项目目录下（项目配置）。

| 命令 | 作用 |
| :--- | :--- |
| `git config --list` | 列出当前配置 |
| `git config --local --list` | 列出repository配置 |
| `git config --global --list` | 列出全局配置 |
| `git config --system --list` | 列出系统配置 |
| `git config --global user.name "your name"` | 配置用户名 |
| `git config --global user.email "youremail@github.com"` | 配置用户邮箱 |
| `git config --global user.password "your password"` | 配置用户密码 |
| `git config --global color.ui auto` | 配置git命令输出为彩色的 |
| `git config --global core.editor vi` | 配置git使用的文本编辑器 |
| `git config --global merge.tool vimdiff` | 配置解决冲突时使用哪种差异分析工具，比如要使用vimdiff |

---

### 四、工作区上的操作命令（Workspace）

1. 新建本地仓库

| 命令 | 作用 |
| :--- | :--- |
| `git init` | 在当前目录新建一个Git代码库 |
| `git init [project-name]` | 新建一个目录，将其初始化为Git代码库 |
| `git clone [url]` | 下载一个项目和它的整个代码历史 |
| `git clone [url] [projec name]` | 克隆远程库，并且重命名项目名称 |

---

2. 提交操作

| 命令 | 作用 |
| :--- | :--- |
| `git add .` | 提交工作区所有文件到暂存区 |
| `git add [file1] [file2] ...` | 提交工作区中指定文件到暂存区 |
| `git add [dir]` | 提交工作区中某个文件夹中所有文件到暂存区（包括子目录） |

3. 撤销操作

| 命令 | 作用 |
| :--- | :--- |
| `git rm [file1] [file2] ...` | 删除工作区文件，并且也从暂存区删除对应文件的记录 |
| `git rm --cached [file]` | 从暂存区中删除文件，但是工作区依然还有该文件 |
| `git reset HEAD [file]...` | 取消暂存区已经暂存的文件 |
| `git checkout --[file]` | 当改乱了工作区某个文件的内容，而且尚未进行add命令，想直接丢弃工作区的修改时使用此命令 |
| `git stash` | 隐藏当前变更，以便能够切换分支 |
| `git stash list` | 查看当前所有的储藏 |
| `git stash apply` | 应用最新的储藏 |
| `git stash apply stash@{0}` | 恢复指定的stash（0代表第一个） |
| `git stash apply --index` | 重新应用被暂存的变更，使用apply命令只是应用储藏，而内容仍然还在栈上，需要移除指定的储藏 |
| `git stash drop stash{0}` | 移除指定的储藏 |
| `git stash pop` | 恢复储藏，并删除stash内容 |

4. 更新操作

| 命令 | 作用 |
| :--- | :--- |
| `git mv [file-original] [file-renamed]` | 重命名文件，并将已改名文件提交到暂存区 |

5. 查询操作

| 命令 | 作用 |
| :--- | :--- |
| `git status` | 查询当前工作区所有文件的状态 |
| `git diff` | 比较工作区中当前文件和暂存区之间的差异，也就是修改之后还没有暂存的内容 |
| `git diff [file-name]` | 指定文件在工作区和暂存区上差异比较 |

---

### 暂存区上的操作命令-

1. 提交文件到版本库

| 命令 | 作用 |
| :--- | :--- |
| `git commit -m [commit info]` | 将暂存区的改动提交到本地仓库，每次提交都会产生一个commit id |
| `git commit [file1] [file2] ... -m [commit info]` | 提交暂存区的指定文件到本地仓库，每次提交都会产生一个commit id |
| `git commit -a` | 将所有已经使用git管理过的文件暂存后一并提交至本地仓库，跳过add到暂存区的过程，每次提交都会产生一个commit id |
| `git commit --amend` | 提交文件时，发现漏掉几个文件，或者注释写错了，可以撤销上一次提交，即amend提供对最后一次commit的反悔，但是如果已经push过了，那么其历史最后一次，永远也不能修改了 |


2. 查看信息

| 命令 | 作用 |
| :--- | :--- |
| `git diff --cached` | 比较暂存区与上一版本的差异 |
| `git diff <file-name> --cached` | 指定文件在暂存区和本地仓库的不同 |
| `git log` | 查看提交历史 |
| `git log -p -2` | 参数-p展开每次提交的内容差异，用-2显示最近的两次更新 |
| `git reflog` | 用来记录每一次命令，即显示整个本地仓储的commit, 包括所有branch的commit, 甚至包括已经撤销的commit, 只要HEAD发生了变化, 就会在reflog里面看得到. git log只包括当前分支的commit |


3. 打标签

| 命令 | 作用 |
| :--- | :--- |
| `git tag` | 列出现在所有的标签 |
| `git tag v1.5` | 创建一个轻量级标签的话，就直接使用git tag命令即可，连-a,-s以及-m选项都不需要，直接给出标签名字即可 |
| `git tag -l "v1.4.2.*"` | 使用特定的搜索模式列出符合条件的标签，例如：这个命令是只对1.4.2系列的版本感兴趣 |
| `git tag -a v1.4 -m "my version 1.4"` | 创建一个含附注类型的标签，需要加-a参数 |
| `git show v1.4` | 使用git show命令查看相应标签的版本信息，并连同显示打标签时的提交对象 |
| `git tag -s v1.5 -m "my signed 1.5 tag"` | 如果有自己的私钥，可以使用GPG来签署标签，只需要在命令中使用-s参数 |
| `git tag -v v1.5` | 验证已签署的标签 |
| `git push origin v1.5` | 将标签推送到远程仓库中 |
| `git push origin --tags` | 将本地所有的标签全部推送到远程仓库中 |

4. 分支管理

| 命令 | 作用 |
| :--- | :--- |
| `git branch [branch-name]` | 创建分支 |
| `git checkout [branch-name]` | 从当前所处的分支切换到其他分支 |
| `git checkout -b [branch-name]` | 新建并切换到新建分支上 |
| `git branch -d [branch-name]` | 删除分支 |
| `git merge [branch-name]` | 将当前分支与指定分支进行合并 |
| `git branch` | 显示本地仓库的所有分支 |
| `git branch -v` | 查看各个分支最后一个提交对象的信息 |
| `git branch --merged` | 查看哪些分支已经合并到当前分支 |
| `git branch --no-merged` | 查看当前哪些分支还没有合并到当前分支 |
| `git merge [remote-name]/[branch-name]` | 把远程分支合并到当前分支。<br>如果是单线的历史分支不存在任何需要解决的分歧，只是简单的将HEAD指针前移，所以这种合并过程可以称为快进（Fast forward），而如果是历史分支是分叉的，会以当前分叉的两个分支作为两个祖先，创建新的提交对象；如果在合并分支时，遇到合并冲突需要人工解决后，再才能提交 |
| `git checkout -b [branch-name] [remote-name]/[branch-name]` | 在远程分支的基础上创建新的本地分支 |
| `git pull` | 在跟踪分支上，拉取远程仓库的变化，并与本地分支合并 |
| `git rebase` | 可以对某一段线性提交历史进行编辑、删除、复制、粘贴，可以把本地未push的分叉提交历史整理成直线。<br>使用rebase操作应该遵循的原则是：一旦分支中的提交对象发布到公共仓库，就千万不要对该分支进行rebase操作。 |
| `git rebase -i  [startpoint]  [endpoint]` | -i的意思是--interactive，即弹出交互式的界面让用户编辑完成合并操作，[startpoint]和[endpoint]则指定了一个编辑区间，如果不指定[endpoint]，则该区间的终点默认是当前分支HEAD所指向的commit(注：该区间指定的是一个前开后闭的区间)。<br>如：`git rebase -i 36224db`或`git rebase -i HEAD~3`<br> |
| `git rebase [rebase-branch] [branch-name]` |  |
| `` |  |
| `` |  |
| `` |  |
| `` |  |
| `` |  |
| `` |  |
| `` |  |


| 命令 | 作用 |
| :--- | :--- |
| `` |  |
| `` |  |
| `` |  |
| `` |  |
| `` |  |
| `` |  |
| `` |  |
| `` |  |


| 命令 | 作用 |
| :--- | :--- |
| `` |  |
| `` |  |
| `` |  |
| `` |  |
| `` |  |
| `` |  |
| `` |  |
| `` |  |
