# GitHub Pages FAQ

See also Hoststar FAQ.

GH Pages is ued both for the Canada Club website and the onierstrasz personal website.

* Q How to configure the footer?

* Q How to add a sidebar?


* Q How does the minima theme work?

https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll

Debugging CSS -- inspect the generated HTML to see that assets/main.css is the imported css file. So assets/main.scss to add stuff.

Minima theme:
https://github.com/jekyll/minima

How to override it:
https://jekyllrb.com/docs/themes/#overriding-theme-defaults

* Q How to use liquid templates? (used by Jekyll)

Learn about the Liquid templating system
https://shopify.github.io/liquid/


* Q How to run on localhost?

Testing your GitHub Pages site locally with Jekyll - GitHub Docs

From zsh, needed:
	bundle add webrick

Then simply:
	bundle exec jekyll serve
 and open http://localhost:4000

