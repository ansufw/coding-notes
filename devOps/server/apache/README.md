# Install Apache

```sh
sudo apt install apache2
```
start apache
```sh
systemctl start apache2
```
check apache status
```sh
systemctl status apache2
```

the initial file for serving the web goes to `/var/www/html/index.html`

# Set virtual host

Create two other dirs in the `/var/www/`

```sh
mkdir /var/www/www
mkdir /var/www/ohas

```
these two folders will be where we store the HTML files associated with the two virtual hosts. Now, we should change the owner of these two folders as well as the permission. Go to the dir `cd /var/www` and run

```sh
sudo chown -R user:user www
sudo chown -R user:user ohas
sudo chmod -R 755 www
sudo chmod -R 775 ohas
```

create two simple `index.html` in both folder for testing purpose whether the web server work to serve the html page or not.


# Configure Apache

Now i need to tell apache about these virtual hosts. so then go to app directory

```sh
cd /etc/apache2  
```
run the `ls` command and there a bunch of files and folder but now we focus on two files `sites-available` and `sites-enabled`.     
The discription of the virtual hosts exist in the `sites-available` and all of the ones that are actually being served exist in `sites-enabled`

So what I need to make my two vitual hosts (www and ohas) active is two configuration files in `sites-available` and the symbolic link in `sites-enabled`   
```sh
cd sites-available
sudo vi ohas.conf
```
put these lines to conf file

```sh
<VirtualHost *:80>
        ServerAdmin me@here.com
        ServerName ohas.halaldev.my.id
        ServerAlias www.ohas.halaldev.my.id
        DocumentRoot /var/www/ohas
        ErrorLog ${APACHE_LOG_DIR}/ohas-error.log
        CustomLog ${APACHE_LOG_DIR}/ohas-access.log combined
</VirtualHost>
```

and do the same thing for virtual host `www`,

```sh
cp ohas.conf www.conf
```

put this lines to `www.conf`.

```sh
<VirtualHost *:80>
        ServerAdmin me@here.com
        ServerName www.halaldev.my.id
        DocumentRoot /var/www/www
        ErrorLog ${APACHE_LOG_DIR}/www-error.log
        CustomLog ${APACHE_LOG_DIR}/www-access.log combined
</VirtualHost>
```

Now we are going to make symbolic link. First go to dir `sites-enabled`,  and run `sudo ln -s /etc/apache2/sites-available/www.conf .`. But there is utility from apache2 to make this job easier by running

```sh
sudo a2ensite path/to/conf_file_name
```
in this case, `sudo a2ensite www.conf` and `sudo a2ensite ohas.conf`.

to exclude enable sites, run

```sh
sudo a2dissite 000-default.conf
```
and reload apache

```
systemctl reload apache2
```

