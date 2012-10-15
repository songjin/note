# Git

## Init

 
	git config --global user.name "Your Name Comes Here"	git config --global user.email you@yourdomain.example.com
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
	
	git show dfb02e6e4f2f7b573337763e5c0013802e392818	git show dfb02 
	git show HEAD # Show now branch's new version	git show HEAD^ # Show HEAD's father	git show HEAD^^ # 查看 HEAD's grandfather	git show HEAD~4 # 查看 HEAD grandfather's grandfather	git tag v0.1 dfb02	
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