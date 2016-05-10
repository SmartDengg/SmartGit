# SmartGit

### Git clone

	$ git clone <版本库的网址>
	
	$ git clone git@github.com:SmartDengg/SmartGit.git

	git init
	rm -rf .git

### git remote

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