# How to start/stop apache
1. to start apache server `sudo apachectl start`
2. to stop apache server `sudo apachectl stop`
3. to view apache version `httpd -v`
4. to configure apache, edit `/etc/apache2/httpd.conf`
5. to use the commands without `sudo` prefix, login to root `sudo su -`
6. to see default documents library, go to `cd /Library/WebServer/Documents`

# How to setup apache in your folder

1. Go to home folder (`cmd+up`)
2. Create a folder called `Sites`
3. Create an `index.html` file with content like `<html><body><h1>This is in the personal folder</h1></body></html>`
4. Edit file config in `sudo nano /etc/apache2/httpd.conf`
  - uncommented lines that contains words `mod_userdir` and `httpd-userdir` by using search feature (`ctrl+w`) in nano
  - press `ctrl+x` and `y` to save the changes
5. Edit file `sudo nano /etc/apache2/extra/httpd-userdir.conf`
  - uncommented a line that contains words `*.conf` by using search feature (`ctrl+w`) in nano
  - press `ctrl+x` and `y` to save the changes
6. Create file `your_username.conf` in the folder `/etc/apache2/users` with this content
```sh
<Directory "/Users/ananto/Sites">
	Options Indexes Multiviews
	AllowOverride None
	Require all granted
</Directory>
```
7. restart apache `sudo apachectl restart`
8. Open your browser and put `localhost/~your_username`
