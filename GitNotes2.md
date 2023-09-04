# Git工作原理

![](image\GitNotes2\git工作原理.png)

Git有三个区域：工作区、暂存区、仓库

1. 工作区（Working Directory)：就是平时修改代码的文件夹部分。
3. 暂存区(Staging Area)：就是git add后的代码会以快照形式存储在暂存区，也就是.git文件夹内。快照理解为代码备份；暂存区理解用来记录代码以及更改的地方。
4. 本地仓库(local repository)：git commit最终提交更改，实际就是把暂存区的内容全部提交到本地仓库中。远程仓库：GitHub、Gitee仓库。

注意理解偏差commit后暂存区的内容是依旧保留的，不要理解成“购物车”的概念。（工作区/暂存区/仓库，它应该理解为一个流程，如果理解为流程过程则可以用购物车去理解暂存区）

为什么要区分暂存区和仓库？因为可以在git commit之前多次git add，将文件添加到暂存区，或者git checkout从暂存区恢复文件。

暂存区理解为草稿纸，完成修改后可以用git commit把之前所有修改提交至仓库，git会提交生成版本号，用来进行最终的版本控制。


# Git四条基础命令

1. `git add <file>      `：文件从工作区增加到暂存区。
2. `git checkout <file> `：从暂存区恢复文件到工作区（add的反向命令）。
3. `git commit <file>-m `：提交暂存区快照到本地仓库。
4. `git reset HEAD <file>`：把暂存区恢复为本地仓库的最新版本（git commit的反向命令）。HEAD 表示当前版本；HEAD^ 上一个版本；HEAD^^ 上上个版本，以此类推。

# Git Bash命令行工具命令

`git init`：此命令初始化一个新本地仓库，它在工作目录下生成一个名为.git的隐藏文件夹。

`git add .` ：.代表当前文件夹；把当前文件夹所有文件及非空文件夹，设置为准备提交状态。

`git add <file>` ：某个文件，将文件设为准备提交状态（索引中的暂存区）。

> git的专业术语：把文件加入暂存区（工作区→add→暂存区→commit→仓库），扩展：暂存区的英文两种表达方式1.index；2.stage。

> 可以把暂存区理解为抽象的文件夹，它的具体实现则在.git文件夹里（理解为是一个流程记录）。暂存区在版本控制软件中并不是必需的，如SVN就没有暂存区 可以把源代码文件从工作区直接提交到仓库。

`git commit -m "feat:新功能"`：回车提交成功后，git会把源代码以数据库的形式保存在仓库中。引号里备注的内容一定要写，不然以后分不清区别了。

`git log`：查看提交的历史记录（会显示Author作者、Date日期时间、备注的内容）

`git checkout HEAD <file>` ：最后（新）一次的commit提交里，把文件复制到工作区（会覆盖）（简单来说就是仓库直接退回上一个版本到工作区）


# 提交代码到远程仓库方法

* 用Visual Studio Code提交代码到远程仓库的方法

方法一：

1. 左侧栏源代码管理
2. 点击+号 暂存更改
3. 消息框输入注释提交
4. 点击左下栏的同步图标
5. 弹出“此操作讲从···中拉取并向其推送提交。”弹窗，点击确定。

方法二：

1. `git add 文件名`：添加文件到索引暂存区，记录更新。
2. `git commit -m "feat: 注释"`：-m只提交add添加的文件到本地仓库；feat:表示开发新功能；fix:修改bug；docs:只改动了文档相关的内容。
3. `git push`：将本地仓库代码推送到远程仓库。

* 命令扩展

`git status`：查看存储库和暂存区的状态。

`git commit -m "feat: 注释"`：提交到库。

`git commit -a "docs: 注释"`：自动把所有被修改的文件添加到索引暂存区，(不包含新建文件)并同时把它们提交。会弹出vim提交信息；fix：修改bug

 `git commit -a -m "fix:修改代码"`：-a -m修改过的都能提交，包含没有add添加到暂存区的文件可以直接提交；docs:只改动了文档相关的内容。

 `git commit -am "fix:修改代码"`：也可以连写，直接提交到版本库（本地仓库）。

 `git commit --amend`：两个作用：1.追加提交，不增加commit记录修改前一次commit，但commit-ID会改变；2.覆盖上一次提交信息，也会生成新的commit-id。amend:修正修订的意思。

`git pull`：取回远程主机某个分支的更新，再与本地的指定分支合并。

`git pull origin master` ：将远程origin主机的master分支拉取过来和本地的当前分支进行合并。

`git pull origin master:brantest` ：git pull <远程主机名> <远程分支名>:<本地分支名>：将远程主机origin的master分支拉取过来，与本地的brantest分支合并。

git fetch和git pull区别：git fetch不会进行合并执行后需要手动执行git merge合并分支，而git pull拉取远程分之后直接与本地分支进行合并。
