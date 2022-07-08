# Git-learning
Learning git and related operations for further work.

这次的学习教程是廖雪峰的官方网站里的Git教程，比较清晰。
https://www.liaoxuefeng.com/wiki/896043488029600

有关笔记和操作记录更新在下方：

介绍
    SVN/CVS
        集中式版本控制系统——图书馆
    Git
        C语言
        分布式版本控制系统
            安全

基操
    本地传github
        建库，用SSH联通
        git init
        git add xxxx.file
        git commit -m "yyyy"
        git push
    github克隆到本地
        git clone git@xxxx
    版本回退
        git status
        靠版本序号，github上也会有history记录
        git reset --hard xxxx
    stage
        暂存区，区别开版本库
        工作区的修改会保存在暂存区，add后才会进入版本库
        修改，add，修改，commit
            只会提交第一次的修改，因为add进去的是第一次的修改
    删除
        恢复：添加到版本库的可以恢复
        rm xxxx.file
        git rm xxxx.file

分支
    创建合并
        靠指针来调整，所以很快速
    git checkout -b xxxx
        创建分支
        git branch xxxx
        git checkout xxxx
    git branch
        查看分支
    git merge xxxx
        合并分支到当前分支
        得在main分支里写这句，相当于省略了merge xxxx (to main)
    git branch -d xxxx
        删除分支
    switch 可代替 checkout 防误用
        git switch -c xxxx
        git switch main
    分支冲突
        修改内容后保存，重新add，commit
    分支管理
        git merge --no-ff -m "merge with no-ff" xxxx
        日常在xxxx分支干活
        发布时，合并到main分支发布1.0版本
    bug分支
        git stash
        git stash list
        git stash pop
            git stash apply
            git stash drop
        git stash apply stash@{0}
        git cherry-pick xxxxxx
            复制一个特定的提交到当前分支
            避免重复劳动
    分支强制删除
        git branch -D xxxx
    多人协作
        多人协作工作模式通常是这样：
            首先，可以试图用git push origin <branch-name>推送自己的修改；
            如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
            如果合并有冲突，则解决冲突，并在本地提交；
            没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！
                如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>
        git remote
        git remote -v
        git clone git@github.com:xxxx/xxxx
        git push origin xxxx
        git pull
        git chechout -b xxxx origin/xxxx
        git branch --set-upstream xxxx origin/xxxx
    变基 rebase
        可以把本地未push的分叉提交历史整理成直线
        使我们在查看历史提交的变化时更容易，分叉的提交需要三方对比

标签
    创建
        git tag v1.0
        git tag
        git show v0.9
        git tag -d v0.1
    操作
        git push origin v1.0
        git push origin --tags
        git tag -d v0.9
        git push origin :refs/tags/v0.9

自定义 Git
    git config --global color.ui true 不同颜色
    .gitignore 忽略特殊文件
    git config --global alias.co checkout 配置别名

cheat sheet
｜ https://liaoxuefeng.gitee.io/resource.liaoxuefeng.com/git/git-cheat-sheet.pdf
