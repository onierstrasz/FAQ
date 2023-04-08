# Apache FAQ

# Q How to start apache?

	sudo apachectl start

# Q How to enable user Sites on Mac?

https://iraspa.org/blog/setting-up-apache-user-sites-folders-on-macos/


Edit 
	/etc/apache2/httpd.conf
and uncomment these lines:

	LoadModule authz_host_module libexec/apache2/mod_authz_host.so
	LoadModule authz_core_module libexec/apache2/mod_authz_core.so
	LoadModule include_module libexec/apache2/mod_include.so
	LoadModule vhost_alias_module libexec/apache2/mod_vhost_alias.so
	LoadModule userdir_module libexec/apache2/mod_userdir.so
	LoadModule rewrite_module libexec/apache2/mod_rewrite.so
	Include /private/etc/apache2/extra/httpd-userdir.conf
	Include /private/etc/apache2/extra/httpd-vhosts.conf

Edit 
	/etc/apache2/extra/httpd-userdir.conf
and uncomment:

	Include /private/etc/apache2/users/*.conf

Add users/*.conf files if missing. Edit them to look like this:

/etc/apache2/users/oscar.conf

	<Directory "/Users/oscar/Sites/">
		AllowOverride All
		Options Indexes MultiViews FollowSymLinks
		Require all granted
	</Directory>


Then run 

	sudo apachectl restart

In a pinch you can also try to modify the lines:

    <IfModule unixd_module>
    User _www
    Group _www
    </IfModule>

to the actual user and group.

## Q How to override DNS lookups?

Edit `/etc/hosts`

Simply add
```
127.0.0.1	scg.unibe.ch
```
No apache restart is needed

For example, to see the old web site on cindy
```
130.92.64.123 scg.unibe.ch
```

You can also then set the DocumentRoot to point to wherever you like.
