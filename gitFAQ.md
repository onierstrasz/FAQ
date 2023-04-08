# git FAQ

* Q How to make a git repo point to a different remote?

Check the current remote:

  git remote -v

Change it

  git remote set-url origin ...

* Q How to reduce the size of a git repo?

You could clean everything and commit to the current state.

http://www.xavierdupre.fr/blog/2017-08-24_nojs.html

