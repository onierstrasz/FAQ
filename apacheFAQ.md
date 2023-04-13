# Apache FAQ

# Q How to start apache?

	sudo apachectl start

# Q How to enable user Sites on Mac?

For Ventura

https://discussions.apple.com/docs/DOC-250006086

You should be able to open [localhost](http://localhost) or [127.0.0.1](http://127.0.0.1) and see **It works!**.

This is defined in `/Library/WebServer/Documents/index.html.en` and is defined as `DocumentRoot` in `/etc/apache2/httpd.conf`.

Next, create a `~Sites` folder in your home directory and create an `index.html` there.

Edit `/etc/apache2/users/xxx.conf` where `xxx` is your username.

Add it, or change it to:
```
<Directory "/Users/xxx/Sites/">
	AllowOverride All
	Options Indexes MultiViews FollowSymLinks
	Require all granted
</Directory>
```

Make a backup of `httpd.conf` and the `extra` folder in `orig` or `backup`.

Edit `/etc/apache2/extra/httpd-userdir.conf` and uncomment line 16
```
Include /private/etc/apache2/users/*.conf
```


Edit `/etc/apache2/httpd.conf` and uncomment these lines:
```
LoadModule cgi_module libexec/apache2/mod_cgi.so 			# 174
LoadModule userdir_module libexec/apache2/mod_userdir.so	# 184
Include /private/etc/apache2/extra/httpd-userdir.conf		# 521
```

NB: PHP Is deprecated and was removed from macOS 12

Run the following command to give the Apache web server access to the Sites folder in your home directory.
```
chmod +a "_www allow execute" ~
```

Test the apache configuration:
```
apachectl configtest
```

Then run:
```
sudo apachectl restart
```

Now you should be able to access `localhost/~xxx`.

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
