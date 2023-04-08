# How to install a git post-receive hook for slack

- Login to yogi as a superuser
- sudo su git
- ~git/cmd/slackit.sh
	- you will be prompted for the repo name and the webhook URL

NB: the slackit.sh script is in the repo users-git-yogi-cmd

---
Instructions adapted from the [git-slack-hook project](https://github.com/chriseldredge/git-slack-hook).

NB: this only works with public channels, not private ones!

- Login to the git account on yogi (login to your account and `sudo su git`)
- `cd ~git/repositories/`*your-repo*`.git/hooks`
- `cp ~/git-slack-hook.txt post-receive`
- `chmod +x post-receive`
- (stay logged in)
- go to <https://my.slack.com/services/new/incoming-webhook> and sign into your slack team
- Select *Add incoming WebHooks integration*
- Copy the WebHook URL (`https://hooks.slack.com/services/...`)
- Return to git@yogi
- `git config hooks.slack.webhook-url 'https://hooks.slack.com/services/...'`

---

Q How to contribute to someone else's github project?

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

---
