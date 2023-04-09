# GitHub Pages FAQ

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

<<<<<<< HEAD
## Q How to deploy a GH Pages repo to a different subdomain?

TO BE TESTED ...

Suppose you have a custom user domain `mydomain.org`.
If you deploy a project `xyz`, it will be mapped to `mydomain.org/xyz`.
If instead you want it to go to `xyz.mydomain.org`, then you must:
(1) Enable GH pages for the repo
(2) Specify the custom domain `example.com` (best if it starts with `www`)
(3) Create 4 `A` records for `185.199.[108-111].153` 
(4) and 1 `CNAME` record for `username.github.io`
(5) Confirm the `A` records by running `dig +noall +answer example.com` (returns the IP addresses) and confirm the `CNAME` record with `dig www.example.com +nostats +nocomments +nocmd` (returns `CNAME username.github.io`)
(6) Check the `Enforce HTTPS` option.

https://stackoverflow.com/questions/9082499/custom-domain-for-github-project-pages

## Q How to get a sitemap?
In the [`docs/_pages`](https://github.com/mmistakes/minimal-mistakes/tree/master/docs/_pages) folder of the master branch you will find a [`sitemap.md`](https://github.com/mmistakes/minimal-mistakes/blob/master/docs/_pages/sitemap.md) and other resources.

## Q How can you include plain HTML files?

Just add them as top-level files or folders (i.e., not within `_pages` or other special folders).


---

# Open questions

