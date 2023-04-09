# git FAQ

## Q How to make a git repo point to a different remote?

Check the current remote:
```
  git remote -v
```
Change it
```
  git remote set-url origin ...
```
## Q How to reduce the size of a git repo?

You could clean everything and commit to the current state.

http://www.xavierdupre.fr/blog/2017-08-24_nojs.html

## Q How to enable issues for a forked project?

When you fork a project, by default it seems you cannot create issues for your fork.
Enable this under `Settings > General > Features > Issues`.

## Q How to contribute a pull request to someone else's github project?

See https://akrabat.com/the-beginners-guide-to-contributing-to-a-github-project/#summary

In the example the remote is git@github.com:zendframework/zend-validator.git
and the fork is git@github.com:akrabat/zend-validator.git

- create a fork of the project (fork button in github)
- clone the fork
	- git clone git@github.com:akrabat/zend-validator.git
- add the original project as an upstream remote
	- cd into the forked repo directory
	- git remote add upstream git@github.com:zendframework/zend-validator.git
- update and create a branch for one piece of work
	- git checkout master
	- git pull upstream master && git push origin master
	- git checkout -b hotfix/readme-update
	- do some stuff
- push the branch
	- git push -u origin hotfix/readme-update
	- NB: The -u flag links this branch with the remote one, so that in the future, you can simply type git push origin.
- create the PR
	- navigate to your fork on github
	- go to the pushed branch
	- click on "compare & pull request"
	- follow any instructions ...
	- click on "create pull request"

