# Git项

开始菜单中会有Git项，菜单下有3个程序：任意文件夹下右键也可以看到对应的程序！

1. Git Bash：Unix与Linux风格的命令行，使用最多，推荐最多
2. Git CMD：Windows风格的命令行
3. Git GUI：图形界面的Git，不建议初学者使用，尽量先熟悉常用命令

# Git一般工作流程

1. 在工作目录中添加、修改文件；  --首先新建文件如 UserMapper.xml
2. 将需要进行版本管理的文件放入暂存区域；  --git add.
3. 将暂存区域的文件提交到git仓库。 --git commit

因此，git管理的文件有三种状态：已修改（modified），已暂存（staged），已提交(committed)


# Git Bash命令行工具命令

* 基本的Linux命令

1. cd：改变目录。
2. cd..回退到上一个目录，直接cd进入默认目录。
3. pwd：显示当前所在的目录路径。
4. Is（ll）：都是列出当前目录中的所有文件，只不过ll（两个ll）列出的内容更为详细。
5. touch：新建一个文件如touch index.js就会在当前目录下新建一个index.js文件。
6. rm:删除一个文件，rm index.js 就会把index.js文件删除。
7. mkdir：新建一个目录，就是新建一个文件夹。
8. rm-r：删除一个文件夹，rm-rsrc删除src目录。 rm-r /：切勿在Linux中尝试，因为会把整个系统都删掉。
9. mv：移动文件，mv index.html src ；index.html是我们要移动的文件，src是目标文件夹，当然，这样写，必须保证文件和目标文件夹在同一目录下。
10. reset：重新初始化终端/清屏。
11. clear：清屏。在windows的清屏是cls。
12. history：查看命令历史。
13. help：帮助。
14. exit：退出。
15. #：表示注释。

* 常用命令：

`git init`：初始化本地仓库

 `git clone`：复制粘贴远程仓库链接：克隆gitee/giehub的文件到本地

 `git add .`：添加所有文件到暂存区

 `git status`：查看所有文件状态

 `git status <filename>`：查看文件指定状态

 `git commit -m "new file hello.txt"`：提交暂存区中的内容到本地仓库，-m 提交信息

`ssh-keygen`：生成ssh,用于Gitee/GitHub上公钥，提交代码时免密登录作用；`ssh-keygen -t rsa`：加密的；生成后有2个文件，.ssh文件夹的id_rsa.pub文件是公钥粘贴去gitee/giehub上。

`git branch`：   查看本地当前有哪些分支

 `git branch -r`：查看远程有哪些分支

 `git branch -a`：查看本地和远程所有分支

 `git branch dev`：新建本地分支,dev开发分支

 `git checkout -b <branch>`：新建一个分支，并切换到该分支

 `git checkout <branch_name>`：切换指定分支

 `git merge <branch>`：合并指定分支到当前分支

 `git branch -d <branch>`：删除指定分支

 `git push origin --delete <branch_name>`：删除远程指定分支


# 版本冲突

多个分支如果并行执行，就会导致我们代码不冲突，也就是同时存在多个版本！
web-api -A (Restful.xx())

web-admin-B会调用A（修改了A的代码！）

web-app-C会调用B和A的代码

如果了冲突了就需要协商即可！

如果同一个文件在合并分支时都被修改了则会引起冲突：解决的办法是我们可以修改冲突文件后重新提交！选择要保留他的代码还是你的代码！

master主分支应该非常稳定，用来发布新版本，一般情况下不允许在上面工作，工作一般情况下在新建的dev分支上工作，工作完后，比如上要发布，或者说dev分支代码稳定后可以合并到主分支master上来。




有道无术、术尚可求。有术无道、止于术！--2022.07.07
