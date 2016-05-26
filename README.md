# SmartGit

### Git clone

	$ git clone <版本库的网址>
	
	$ git clone git@github.com:SmartDengg/SmartGit.git

	git init
	rm -rf .git

### Git remote

为了便于管理，Git要求每个远程主机都必须指定一个主机名。git remote命令就用于管理主机名。

不带选项的时候，git remote命令列出所有远程主机。

	$ git remote
	origin

使用-v选项，可以参看远程主机的网址。

	$ git remote -v
	origin  git@github.com:SmartDengg/SmartGit.git (fetch)
	origin  git@github.com:SmartDengg/SmartGit.git (push)

上面命令表示，当前只有一台远程主机，叫做origin，以及它的网址。

克隆版本库的时候，所使用的远程主机自动被Git命名为origin。如果想用其他的主机名，需要用git clone命令的-o选项指定。

	$ git clone -o host git@github.com:SmartDengg/SmartGit.git
	$ git remote
	host

上面命令表示，克隆的时候host。

	$ git remote show <主机名>

- git remote add命令用于添加远程主机。

		$ git remote add <主机名> <网址>

- git remote rm命令用于删除远程主机。

		$ git remote rm <主机名>

- git remote rename命令用于远程主机的改名。

		$ git remote rename <原主机名> <新主机名>

- Create a new repository on the command line

		echo "# SmartGit" >> README.md
		git init
		git add README.md
		git commit -m "first commit"
		git remote add origin git@github.com:SmartDengg/SmartGit.git
		git push -u origin master

- Push an existing repository from the command line

		git remote add origin git@github.com:SmartDengg/SmartGit.git
		git push -u origin master

**加上了-u参数，Git不但会把本地的master分支内容推送的远端的master分支，还会把本地的master分支和远端的master分支关联起来，在以后的推送或者拉取时就可以简化命令。**

[adding-a-remote](https://help.github.com/articles/adding-a-remote/)

[removing-a-remote](https://help.github.com/articles/removing-a-remote/)

[renaming-a-remote](https://help.github.com/articles/renaming-a-remote/)

[pushing-to-a-remote](https://help.github.com/articles/pushing-to-a-remote/) include *Renaming branches*

[正常的工作流程](http://gitbook.liuhui998.com/3_2.html)


### 撤销

**撒销一个合并**

如果你觉得你合并后的状态是一团乱麻，想把当前的修改都放弃，你可以用下面的命令回到合并之前的状态：

	$ git reset --hard HEAD

或者你已经把合并后的代码提交，但还是想把它们撒销：

	$ git reset --hard ORIG_HEAD


**撤销指令**

	# 恢复暂存区的指定文件到工作区
	$ git checkout [file]

	# 恢复某个commit的指定文件到暂存区和工作区
	$ git checkout [commit] [file]

	# 恢复暂存区的所有文件到工作区
	$ git checkout .

	# 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
	$ git reset [file]

	# 重置暂存区与工作区，与上一次commit保持一致
	$ git reset --hard

	# 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
	$ git reset [commit]

	# 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
	$ git reset --hard [commit]

	# 重置当前HEAD为指定commit，但保持暂存区和工作区不变
	$ git reset --keep [commit]

	# 新建一个commit，用来撤销指定commit
	# 后者的所有变化都将被前者抵消，并且应用到当前分支
	$ git revert [commit]

	# 暂时将未提交的变化移除，稍后再移入
	$ git stash
	$ git stash pop



##创建分支并建立追踪关系

	# 新建一个分支，与指定的远程分支建立追踪关系
	$ git branch --track [branch] [remote-branch]




	# 新建一个分支，并切换到该分支
	$ git checkout -b [branch]


	#push并建立追踪关系
	"The current branch dev2 has no upstream branch.To push the current branch and set the remote as upstream, use:
	# 1.7.0	
	$ git push --set-upstream [host] [remote-branch]
	# 或者1.8.0
	$ git push -u [host] [remote-branch]


	#如果远程不存在指定分支名，则创建新分支，但不建立追踪关系
	$ git push [host] [local-branch]:[remote-branch]

	#建立追踪关系，在现有分支与指定的远程分支之间
	# Git 1.7.0
	$ git branch --set-upstream [branch] [host]/[remote-branch]
	# 或者Git 1.8.0
	$ git branch -u [host]/[remote-branch] [branch]
	# Git 1.8.0全路径写法
	$ git branch --set-upstream-to=[host]/[remote-branch] [branch]

	_____________________________________
	Given a branch foo and a remote upstream:
	
	#As of Git 1.8.0:
	
	$ git branch -u upstream/foo

	#Or, if local branch foo is not the current branch:
	$ git branch -u upstream/foo foo

	#Or, if you like to type longer commands, these are equivalent to the above two:
	$ git branch --set-upstream-to=upstream/foo
	
	$ git branch --set-upstream-to=upstream/foo foo
	#As of Git 1.7.0:
	
	$ git branch --set-upstream foo upstream/foo

	

	