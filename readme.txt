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






