# Git + Slack FAQ

## Q How to install a git post-receive hook for slack?
NB: These were the steps on the old server yogi. To be adapted for other setups.

- Login to yogi as superuser
```
sudo su git
~git/cmd/slackit.sh
```
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

