git init: 将当前目录初始化为Git可以管理的仓库
git add file： 将file从工作区添加到暂存区
git commit -m "descript": 将暂存区中所有的文件提交到版本库
git status：显示当前仓库的状态，如果没提交到暂存区，则文件显示为红色，如果文件提交到暂缓区，未提交到版本库，则文件为绿色
git diff file： 显示file在工作区和暂存区的区别
git diff --cached file : 显示file在暂存区和版本区的区别
git diff HEAD: 显示file工作区和版本区的区别
git log： 显示从最近到最远的提交的记录，主要用于确定回退到哪个版本
git reflog： 显示命令历史，以便确定要回到未来哪个版本
git reset --hard 版本号：回头到某一个版本号
git checkout --file： 丢弃工作区的修改
git rm file ：删除file
git checkout -- file: 如果误删了file，并且提交了，可以使用此把误删的文件恢复到版本库最新版本

git remote add origin git@github.com:michaelliao/learngit.git： 关联本地库到远程库
git push -u origin master ： 第一次推送master分支的所有内容
git push origin master：此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改
git clone git@github.com:huangyugui/learngit.git: 克隆一个仓库

git branch :查看分支
git branch <name>: 创建分支
git checkout <name>: 切换分支
git checkout -b <name>: 创建并切换分支
git merge <name>： 合并某分支到当前分支
git branch -d <name>: 删除分支
git log --graph --pretty=oneline --abbrev-commit：可以看到分支合并的情况
git merge --no-ff -m "merge with no-ff" dev： 不使用fast-forward模式进行merge

git stash: 将当前工作现场存储起来，如果多次，则会覆盖前一次的
git stash list：显示存储的工作现场
git stash apply <stash> : 恢复当前的工作现场
git stash drop <stash>: 删除工作现场
git stash pop： 恢复工作现场，并删除工作现场


修改bug的流程：
1： $ git stash

2： $ git checkout master
   $ git checkout -b issue-101
    //去文件里修bug
    $ git add README.md
    $ git commit -m "fix-issue-101"

3： $ git checkout master
   $ git merge --no-ff -m "m-merge-issue-101" issue-101
   $ git branch -d issue-101

4： $ git checkout dev
    $ git merge --no-ff -m "dev-merge-m" master

5： $ git stash pop
            //提示冲突，去文件手动改正
            Auto-merging README.md
            CONFLICT (content): Merge conflict in README.md

6： //继续开发 ... ... ，完成后一并提交
    $ git add README.md
    $ git commit -m "fixconflict & append something"

7： $ git checkout master
    $ git merge --no-ff -m "m-merge-dev" dev
    $ git branch -d dev
	
	
git remote： 查看远程库的信息
查看远程库信息，使用git remote -v；
本地新建的分支如果不推送到远程，对其他人就是不可见的，所以可以试图用git push origin branch-name推送自己的修改

多人协作的工作模式通常是这样：
首先，可以试图用git push origin branch-name推送自己的修改；
如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
如果合并有冲突，则解决冲突，并在本地提交；
没有冲突或者解决掉冲突后，再用git push origin branch-name推送就能成功！
如果git pull提示“no tracking information”，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream branch-name origin/branch-name
如果提示 --set-upstream已被弃用并将被移除则使用：git branch --set-upstream-to=origin/dev dev



从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交
在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；
（如果上面一步报错：fatal: Cannot update paths and switch to branch 'dev' at the same time.
Did you intend to checkout 'origin/dev' which can not be resolved as commit?
则可以git remote show origin   、   git remote update，然后在执行上面的操作）


git tag <name>： 新建一个标签
git tag： 列出所有的标签
git tag -a <标签名> -m <文字说明> <commit id> 
git push origin <tagname>：可以推送一个本地标签；
git push origin --tags：可以推送全部未推送过的本地标签；
git tag -d <tagname>：可以删除一个本地标签；
git push origin :refs/tags/<tagname>：可以删除一个远程标签。
git push origin --delete tag <tagname>:可以删除一个远程标签


