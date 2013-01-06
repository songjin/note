# Git

## Init

 
	git config --global user.name "Your Name Comes Here"
	git config --global user.email you@yourdomain.example.com
## Add
	git add . 
	git add somefiles

## Commit

	git commit 
	git commit -m"with some message"
	git commit -a  # Auto tract file that already add
	
## .gitignore 

	echo "zh" > .gitignore # ignore the zh dir
	
## Git log
	
	git log
	git log --stat --summary # look version's change
	
	git show dfb02e6e4f2f7b573337763e5c0013802e392818
	git show dfb02 
	git show HEAD # Show now branch's new version
	git show HEAD^ # Show HEAD's father
	git show HEAD^^ # 查看 HEAD's grandfather
	git show HEAD~4 # 查看 HEAD grandfather's grandfather

	git tag v0.1 dfb02	
	git show	
	
## Branch

	git branch local # add the "local" branch
	git branch # show the branch
	git checkout local # switch to local
	
	git checkout master
	git merge local
	git branch -d local # delete local if merge
	git branch -D local # delete 
	
## git revert
	git revert commit-id #恢复历史版本
	
## git reset 
	git reset commit-id #重置为历史状态


git 导出

<http://stackoverflow.com/questions/160608/how-to-do-a-git-export-like-svn-export>

	Probably the simplest way to achieve this is with git archive. If you really need just the expanded tree you can do something like this.

	git archive master | tar -x -C /somewhere/else
	Most of the time that I need to 'export' something from git, I want a compressed archive in any case so I do something like this.

	git archive master | bzip2 >source-tree.tar.bz2
	ZIP archive:

	git archive --format zip --output /full/path/to/zipfile.zip master 
	git help archive for more details, it's quite flexible.