# GitHub Pages FAQ

## To do
Provide some structure to this FAQ ...

## Q How to update the templates? (open)

The website is a clone of the academicpages repo. How can we get updates without breaking stuff?

## Q How to set up a GitHub Pages repo?

Any repo can be a GH pages site. You can have just one user site which must be defined in a repo called `username.github.io`, but any other repo can be a GHP site as well. 

By default your user site is deployed at `https://username.github.io` but you can also have it deployed at a custom url. (For this you also need. to register the CNAME record with your provider so your URL will be redirected.)

All other project repos will be mapped to sub-domains of your main user site.

## Q How is content defined?

You must have an `index.html` or `index.md`.

Content is usually defined in `file.md` markdown files with YAML front matter headers. The headers should define the Title of the page. Depending on the theme, they can define a permalink, page layout, and lots of other stuff.

## Q What themes should be used?

You can have a naked site, or you can use one of countless themes.

**NB:** If you use a theme, it's a good idea to initialize your website repo as a fork of the theme, and then put your content and modifications on a branch called `gh-pages`. You should protect the `master` branch from direct modifications.

- [Minima](https://github.com/jekyll/minima) is a simple theme that can be easily adapted to your needs. It is used by the [Canada Club website](https://canadaclub.ch) defined in [this repo](https://github.com/canadaclub/canadaclub.github.io).

- [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) is a richer theme that provides both pages and a blog that have a sidebar of social media links or custom content.

- [Academic Page](https://github.com/academicpages/academicpages.github.io) extends minimal mistakes with sections for Publications, Teaching, Talks and CV. It can also be easily configured. I use it for my [home page](https://www.oscar.nierstrasz.org). It's defined in the [onierstrasz.github.io](https://github.com/onierstrasz/onierstrasz.github.io) repo.

## Q How to configure a Minimal Mistakes GH pages site

GH repo:
https://github.com/mmistakes/minimal-mistakes

Instructions:
https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/

Sidebar doc:
https://mmistakes.github.io/minimal-mistakes/docs/layouts/#sidebars
https://github.com/mmistakes/minimal-mistakes/issues/1322

### Steps

- Fork the minimal mistakes repo
- Create a `gh-pages branch`; make it the default branch
- Protect the main branch
- Remove unneeded files from the gh-pages branch-
- Configure the `_config.yml`: title, author etc.
- Update the `_data/navigation.yml`
- Disable the sidebar or make a custom one.
- Hide the feed in the footer `atom_feed.hide : true`
- Add pages in the `_pages` folder

I tried this on a [Recipes test site](https://github.com/onierstrasz/recipes.github.io)

## Q How to work with pages?

https://mmistakes.github.io/minimal-mistakes/docs/pages/

Add a `_pages` folder.
Add a `permalink` in the yaml front matter of each file.
Remove the default root `index.html`.

## Q Which variables should be defined in the YAML front matter of a page?

```
---
title: Page title
permalink: /path/
---
```

Others:
```
layout: page
author_profile: false
toc: true
redirect_from: 
  - /about/
  - /about.html
```

You can also configure default values for pages (like posts) in the `_config.yml`

## Q How to get rid of the underlines on the URLs?

Add this to `_sass/minimal-mistakes/_page.scss`

```
body {
	a { text-decoration: none !important; }
}
```

## Q How to disable the Sidebar?
In `_config.yml` set `author_profile: false`
Also set all author attributes to nil (not empty strings).

Also modify `_sass/minimal-mistakes.scss` to add:
```
/* added this to disable the sidebar */
article.page {
  float: left;
  width: 100%;
}
```

## Q How to configure a custom sidebar?

You can add the following either to the front matter of a single page, or to the defaults for `pages` in `_config.yml` under `values:`

```
sidebar:
  - title: "Nierstrasz Family website"
    image: /assets/images/crest-small.jpg
    text: "some sample text"
  - title: "another title"
    text: "more text"
```

https://mmistakes.github.io/minimal-mistakes/docs/layouts/#sidebars

Examples

https://mmistakes.github.io/minimal-mistakes/layout-sidebar-custom/

https://mmistakes.github.io/minimal-mistakes/layout-sidebar-nav-list/

## *** Q How to get a TOC in the sidebar?

I'd like a table of contents for the page based on the headers. How is this generated?

https://mmistakes.github.io/minimal-mistakes/docs/helpers/

For an example, see [identify the champion](https://www.oscar.nierstrasz.org/champion/)

NB:I could not get the toc flag in the YAML header to work.
Instead I used the deprecated method:

```
{% include toc icon="cog" title=" " %}
```

To fix the width, see [table of contents do not look well](https://github.com/academicpages/academicpages.github.io/issues/221)

## Q How to use liquid templates? (used by Jekyll)

Learn about the Liquid templating system
https://shopify.github.io/liquid/


## Q How to run on localhost?

Testing your GitHub Pages site locally with Jekyll - GitHub Docs

From zsh, needed: bundle add webrick

Then simply:

```
bundle exec jekyll serve
```

and open http://localhost:4000

## Q How to deploy a GH Pages repo to a different subdomain?

Did this for www.test.nierstrasz.org and www.family.nierstrasz.org

Suppose you have a custom user domain `mydomain.org`.
If you deploy a project `xyz`, it will be mapped to `mydomain.org/xyz`.
If instead you want it to go to `xyz.mydomain.org`, then you must:

1. Enable GH pages for the repo
2. Specify the custom domain `example.com` (best if it starts with `www`)
3. Create 4 `A` records for `185.199.[108-111].153` 
4. and 1 `CNAME` record for `username.github.io`
5. Confirm the `A` records by running `dig +noall +answer example.com` (returns the IP addresses) and confirm the `CNAME` record with `dig www.example.com +nostats +nocomments +nocmd` (returns `CNAME username.github.io`)
6. Check the `Enforce HTTPS` option.

https://stackoverflow.com/questions/9082499/custom-domain-for-github-project-pages

## Q How to get a sitemap?
In the [`docs/_pages`](https://github.com/mmistakes/minimal-mistakes/tree/master/docs/_pages) folder of the master branch you will find a [`sitemap.md`](https://github.com/mmistakes/minimal-mistakes/blob/master/docs/_pages/sitemap.md) and other resources.

## Q How can you include plain HTML files?

Just add them as top-level files or folders (i.e., not within `_pages` or other special folders).

## Q How to set up a photo gallery?

The easiest way is just to put images inside markdown tables.
If you just want a row of images with captions, a trick is to put the images in the header.
Make the images clickable and point to a page with the full image.

NB: The columns are adjusted to the width of the text, so make those equal.

## Q How to get an edit button?

Add the link to the f`_includes/footer.html` with a pencil icon.
Possibly add some CSS to put it at the right.
To get the file path, access `{{page.path}}`
(at least according to the [jekyll docs](https://jekyllrb.com/docs/variables/)).

```
<a href="{{site.repository}}/edit/gh-pages/{{ page.path }}"><image src="/images/pencil-grey-bg.png" alt="edit" width="20" length="20"></a>
```

*NB:* If the layout has `{% include_cached footer.html %}` then you must change it to `{% include footer.html %}` or else the `page` variable will not be correct!

## Q How to add Google Analytics?

Create an account on https://analytics.google.com/

Note the tracking tag to be added manually.

Add this to the config.yml

```
analytics:
  provider: "custom"
  google:
    tracking_id: "G-7EH2V961E8" # Replace by the actual tag
    anonymize_ip: false # default
```

Add the gtag snippet to `_includes/analytics-providers/custom.html`.
Copy-paste from the analytics site with the correct tag.

```
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-7EH2V961E8"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-7EH2V961E8');
</script>
```

## Q How to add the Mastodon link on the author profile?

Same instructions for Bluesky

- Add author.mastodon URL to `_config.yml`
- Add `$mastodon-color : #5e22c5;` to `_sass/_variables.scss`
- Add `.fa-mastodon,.fa-mastodon-square` to `_sass/_utilities.scss`
- Add new line to `_includes/author-profile.html`
- Posssibly update or replace the `_sass/vendor` folder and relevant parts of the `assets` folder. (NB: there are some custom assets in `assets/images` -- don't trash those.)

---

## Q How to test a Jekyll site on localhost?

https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll

First install Ruby, then Jekyll on a mac.

```
brew install chruby ruby-install xz
ruby-install ruby 3.1.3
```

NB: The latest version now is 3.2.2

```
brew install chruby ruby-install xz
ruby-install ruby 3.2.2
```

Run this script from the project folder to serve the website from `http://localhost:4000`

```
#! /bin/bash
# Run this script from the project folder

cd `dirname "$0"`

# load ruby
source /usr/local/opt/chruby/share/chruby/chruby.sh
source /usr/local/opt/chruby/share/chruby/auto.sh
chruby ruby-3.1.3

# install jekyll
gem install jekyll

# create Gemfile
cat > Gemfile <<'eof'
source 'https://rubygems.org'
gem 'nokogiri'
gem 'rack', '~> 2.2.4'
gem 'rspec'
gem 'jekyll'
gem 'jekyll-paginate'
gem 'jekyll-sitemap'
gem 'jekyll-gist'
gem 'jekyll-feed'
gem 'jekyll-include-cache'
eof

bundle install
# git add Gemfile Gemfile.lock

# start the server
bundle exec jekyll serve

# Or tracing mode
# bundle exec jekyll serve --trace

# You can now open http://localhost:4000
```

NB: If you get errors, you may have to install more gems in the script.
NB: You shouldn't push changes to the Gemfile to the repo. It's a good idea to make a backup and restore it.

# How do I create a draft post?

https://jekyllrb.com/docs/posts/

Put it in the drafts folder and run `jekyll serve --drafts`
