# PHP FAQ

---

# How to install PHPUnit

- install Pear
- install PHPUnit
- configure NetBeans
- install XDebug

---

# Install Pear

- uncomment LoadModule php5_module in `/etc/apache2/httpd.conf`
- restart apache (`sudo apachectl restart`)
- `curl http://pear.php.net/go-pear.phar > go-pear.phar`
- `sudo php go-pear.phar`
- Enter 'all' to change install location to /usr/local/pear
- Add `/usr/local/pear/bin/pear` to your (bash/tcsh) PATH
- Check if `/etc/php.ini` correctly specifies the include path
     include_path=".:/usr/local/pear/share/pear"
     (should be done already by go-pear)
- Run `php -i | grep include_path` and check that all is ok
- Run `pear help` to check that it works.
- If necessary, set the proxy server for pear
     `pear config-set http_proxy http://username:password@yourproxy:80`

## Instructions (partly outdated)
- <http://www.newmediacampaigns.com/page/install-pear-phpunit-xdebug-on-macosx-snow-leopard>
- Incomplete: <http://clickontyler.com/blog/2008/01/how-to-install-pear-in-mac-os-x-leopard/>

---


# Install PHPUnit

	sudo pear channel-discover pear.phpunit.de
	sudo pear channel-discover components.ez.no 
	sudo pear channel-discover pear.symfony-project.com
	sudo pear install phpunit/PHPUnit

You should now find PHPUnit installed here:

- `/usr/local/pear/share/pear/PHPUnit`

There should also be an executable here:

- `/usr/local/pear/bin/phpunit`

## Instructions
- <https://github.com/sebastianbergmann/phpunit/#readme>
- PHPUnit book: <http://www.phpunit.de/manual/3.5/en/phpunit-book.pdf>

---

# Configure Netbeans (Mac OSX)


- Open NetBeans>Preferences>PHP>Unit Testing
- Set PHPUnit script to `/usr/local/pear/bin/phpunit`

To use PHPUnit, you must add a test folder to your project:

- Right-click on the project root and select New>Folder
- Create a folder called (say) "tests"
- Right-click on the project root and select "Properties"
- Set the test folder to the newly created folder
- Right-click on a project file and select Tools>Create PHPUnit tests to generate a skeleton test case

---

# Install XDebug

Run `php -i` and dump output into <http://xdebug.org/find-binary.php>

- Download `http://xdebug.org/files/xdebug-2.1.1.tgz`
- Unpack the downloaded file with tar -xvzf xdebug-2.1.1.tgz
- Run: `cd xdebug-2.1.1`
- Run: `phpize`
- Run: `./configure`
- Run: `make`
- Run: `cp modules/xdebug.so /usr/lib/php/extensions/no-debug-non-zts-20090626`

Update `/etc/php.ini` with the right path to xdebug.so:

	zend_extension = /usr/lib/php/extensions/no-debug-non-zts-20090626/xdebug.so
	xdebug.remote_enable=on
	xdebug.remote_log="/var/log/xdebug.log"
	xdebug.remote_host=localhost
	xdebug.remote_handler=dbgp
	xdebug.remote_port=9000

- restart apache (`sudo apachectl restart`)

Now you should be able to right-click>Debug a php file from NetBeans

## Instructions
- <http://wiki.netbeans.org/HowToConfigureXDebug#How_to_on_MAC_OSx_Snow_Leopard>

---


