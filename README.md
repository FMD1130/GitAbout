# Git说明
---

### 一、专用名词
版本库：`.git文件夹`，里面包含两部分：暂存区和本地仓库；
1. Workspace：<br>
工作区，本地电脑存放项目文件的地方；
2. Index/Stage：<br>
暂存区，存在于`.git文件夹`，存放临时文件，用来准备一个提交，但可以不用把工作目录中所有的修改内容都包含进来。这样你可以创建一个高度聚焦的提交，尽管你本地修改很多内容。使用add命令之后，将工作区的改动文件添加到此处；
3. 本地仓库：<br>
存在于`.git文件夹`，是各个分支存储处，包括git自动创建的master分支，使用commit命令可以将暂存区中的文件添加到本地仓库中；
4. 远程仓库：<br>
存在于git服务器。

![仓库之间的操作](https://github.com/gycold/GitAbout/blob/master/pictures/仓库之间的操作 "仓库之间的操作")
