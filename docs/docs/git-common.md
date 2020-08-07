# GIT 常用命令

1、检验是否安装git: git

2、将本地目录变成git仓库：git init

3、添加文件：git add <file>

4、提交文件到仓库并且添加说明：git commit -m <message>

5、查看git仓库的数据变化：git status

6、往回查看版本日志：git log

7、往未来查看版本日志：git reflog

8、回退到某个一个版本：git reset --hard <版本号>

9、往后回退到上一个版本：git reset --hard HARD^ 

10、往后回退到上上一个版本：git reset --hard HARD^^ 依此类推

11、暂存区： 用git add把文件添加进去，实际上就是把文件修改添加到暂存区

12、用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支

13、工作区：.git文件夹的上一级文件夹

14、跟踪修改：每次修改，如果不用git add到暂存区，那就不会加入到commit中。

15、撤消修改：(1)如果没有添加到暂存区：git checkout -- 文件名
            (2)如果已经添加到暂存区：首先 git reset HEAD 文件名 然后 git checkout -- 文件名

16、删除文件：git rm <file>  git commit -m <message>
    如果工作区文件误删：git checkout -- <file>
    如果仓库文件误删：git checkout HEAD -- <file>

17、使用github当作远程仓库
	(1)创建公钥 ssh-keygen -t rsa -C <email>
	(2)将本地仓库关联远程库 git remote add origin git@github.com:toyotaAE86/git-help.git
	(3)推送本地数据到远程 git push -u origin master
      将本地的master分支推送到origin主机，同时指定origin为默认主机，后面就可以不加任何参数使用git push了

18、查看分支：git branch

    创建分支：git branch <name>
    
    切换分支：git checkout <name>
    
    创建+切换分支：git checkout -b <name>
    
    合并某分支到当前分支：git merge <name>
    
    删除分支：git branch -d <name>

19、合并分支并且禁用Fast forward：  git merge --no-ff -m "merge with no-ff" dev

20、储藏工作现场：git stash

21、查看远程库信息，使用git remote -v；

    本地新建的分支如果不推送到远程，对其他人就是不可见的；
    
    从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；
    
    在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；
    
    建立本地分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name；
    
    从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。

22、查看历史提交的信息：git log --pretty=oneline --abbrev-commit

23、命令git tag <tagname>用于新建一个标签，默认为HEAD，也可以指定一个commit id；

    命令git tag -a <tagname> -m "blablabla..."可以指定标签信息；
    
    命令git tag可以查看所有标签。
    
    命令git push origin <tagname>可以推送一个本地标签；
    
    命令git push origin --tags可以推送全部未推送过的本地标签；
    
    命令git tag -d <tagname>可以删除一个本地标签；
    
    命令git push origin :refs/tags/<tagname>可以删除一个远程标签。
24、删除远程目录或者文件 而保留本地
    git rm -r --cached <目录或者文件>
    git commit -m <msg>
    git push
25、第一次抓取远程仓库中的代码，由于仓库中已经存在代码
    git pull --rebase origin master