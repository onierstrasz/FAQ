---
# WordPress FAQ

## Q How do I install WordPress?

Example: installed cafberna wordpress

- download latest version wordpress.org
- download and install mysql and mysql workbench
- download phpmyadmin; install in ~oscar/Sites
  - <http://www.coolestguidesontheplanet.com/installing-phpmyadmin-on-mac-osx-10-7-lion/>

- login to mysql and initialize the root password
  - mysql -u root -p [no pwd]
  - <http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html>
- use myphpadmin to create database and user
  - create db caf; user wordpress / `password`
  - NB: make sure the host for user wordpress is "localhost"!
  - create the wp_config.php file
- initialize wordpress
  - site cafberna; user admin / `password`

- created git repo "cafberna"
- installed twenty ten theme
- added simple-page-ordering plugin

## Q How do I fix a broken site URL?

- login to myPHPadmin and fix the siteurl in the wp_options table
	https://codex.wordpress.org/Changing_The_Site_URL

## Q How do I administer mySQL?

Use the myphpadmin interface: http://www.jot.fm/phpMyAdmin/

## Q How do I dump and restore a DB table?

backup: `mysqldump -u root -p[root_password] [database_name] > dumpfilename.sql`

restore: `mysql -u root -p[root_password] [database_name] < dumpfilename.sql`

## Q How do I update the WordPress installation?

Do it manually by copying individual files. Keep the old wp-config.php as well as the wp-content subfolders as well as any other custom files.

See: http://codex.wordpress.org/Updating_WordPress#Manual_Update

## Q How do I update the themes and plugins?

Download them directly and unzip them into the themes and plugins folders inside wp-content.

## Q How do I add a twitter feed?

Use the Twitter widget tool to generate the required HTML and paste it wherever you like. https://twitter.com/settings/widgets/

## Q How do I add a Facebook feed?

Combine the following two to have both a full event with photo and a list of following events.

This one is ok but photos only with pro version:
https://wordpress.org/plugins/custom-facebook-feed/

Useful to show a single event from the List of Events:
https://wordpress.org/plugins/feed-them-social/

Very nice! NB: requires PHP 5.4
https://wordpress.org/plugins/facebook-events-widget/

Works but layout is ugly; requires premium for events only:
https://wordpress.org/plugins/facebook-feed/

Annoying and clumsy -- did not succeed to install:
https://wordpress.org/plugins/pixelyoursite/

Only support a specific event; confusing documentation:
https://wordpress.org/plugins/wp-embed-facebook/

Only support pages, not events:
https://wordpress.org/plugins/wp-facebook-feed/
https://wordpress.org/plugins/recent-facebook-posts/
https://wordpress.org/plugins/simple-facebook-plugin/installation/

Fails (PHP error):
https://wordpress.org/plugins/add-facebook/

## Q How to include an Exhibit in a Wordpress page

Install this plugin:

https://wordpress.org/plugins/per-page-add-to/

Configure to allow individual pages to have custom headers.

Add the header code, eg:
```
	<script src="http://api.simile-widgets.org/exhibit/STABLE/exhibit-api.js" ></script>
	<link rel="exhibit/data" data-ex-converter="googleSpreadsheets" type="application/jsonp" href="https://spreadsheets.google.com/feeds/list/1hlo4G2wq_fHpl4X6LWIwqLO2Cwj88M8JM4mYVms5VGc/od6/public/basic?hl=en_US&alt=json-in-script"/>
```

## How do I set up a static home page?

You have to create at least a couple of pages, and then you can set the home page to be a static page.

---

