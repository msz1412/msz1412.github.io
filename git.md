## 创建版本库 ##
    初始化：git init
    添加到暂存区：git add file
    提交到仓库：git commit -m '版本信息'
    查看状态：git status
## 版本回退 ##
    显示提交日志：git log
    记录每一条命令：git reflog
    回退：git reset --hard HEAD^ 或者 git reset --hard 版本号
## 管理修改 ##
    先git add再git commit提交到版本库
    查看工作区和版本库内容区别：git diff -- file
## 撤销修改 ##
    撤销工作区修改(让这个文件回到最近一次git add或者git commit状态)：git checkout -- file
    将暂存区的修改回退到工作区：git reset HEAD file
##  删除文件##
    删除：git rm file;
    git commit;
    恢复：git checkout --file
## 创建于合并分支 ##
    创建：git branch 分支名
    切换：git checkout 分支名;git switch 分支名
    创建并切换：git checkout -b 分支名;git switch -c 分支名
    查看所有分支：git branch
    将分支合并到当前分支：git merge 分支名
    删除分支：git branch -d 分支名
	强行删除没有被合并的分区：git branch -D 分支名
## 解决冲突 ##
    修改提交
## 分支管理策略 ##
    禁用fast forward合并:git merge ---no-ff -m '提交信息' 分支名
    相当于合并后创建一个新的commit
## bug分支 ##
	活干到一半，没法提交，想要新建分支修复bug
    保存现场：git stash
    查看保存的现场：git stash list
    恢复stash（恢复之后删除stash)：git stash pop
	恢复stash(不删除）:git stash apply
    删除stash:git stash drop
    复制特定的提交到当前分支：git cherry-pick commit-id
## 多人协作 ##
    查看远程库信息：git remote -v
    推送分支：git push 远程分支 本地分支
### 多人协作工作模式 ###
1. 查看远程信息库：`git remote -v`
2. 若推送失败，先`git pull`,在试图合并
3. 如果合并有冲突，则解决冲突，并在本地提交
4. 没有冲突或者解决掉冲突后，用`git push origin 分支名`推送
5. 如果`git pull`提示`no tracking infomation`，说明本地分支和远程分支的连接关系没有创建，用命令`git branch --set-upstream-to 本地分支名 origin/远程分支名`
6. 在本地创建和远程分支对应的分支`git checkout -b 本地分支名 origin/远程分支名`
##  Rebase##
- rebase操作可以把本地未push的分叉提交历史整理成直线
- rebase的目的使得我们在查看历史提交变化时更容易，因为分叉的提交需要三方对比
