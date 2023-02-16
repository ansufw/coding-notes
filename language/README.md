When i was child, my father give me book about visual basic.. then i continue learning Pascal when i was in senior highschool. But my bachelor and master degree was not in computer science degree. Fortunately, I married with woman that call me to back pursue my dream as a software engineer () 

# Fullstack languages
1. JavaScript

# Compiler Languages
1. Go
2. C++

## Installing Go

tested in Debian 10.
Execute these following lines on the terminal

```bash

# preparation
sudo apt update
sudo apt install curl

# choose version
version=1.17.4

# download go
curl -O https://dl.google.com/go/go$version.linux-amd64.tar.gz

# extract tarball
tar xfv go$version.linux-amd64.tar.gz
# note: x for extract, f for filename and v for verbose

# Recursively change the owner and group of this directory into root and move to /usr/local
sudo chown -R root:root ./go
sudo mv go /usr/local

# setting path
nano ~/.bashrc

# add the folling lines to .bashrc and save it
GOPATH=$HOME/work
PATH=$PATH:/usr/local/go/bin:$GOPATH/bin

# refresh by running
source ~/.bashrc

# testing
go version

```

alternatively, put the lines to file, say `installer.sh`, set the execute permission using `chmod +x` and run the script using `./installer.sh` or `bash installer.sh` or `sh installer.sh`

reference : https://www.digitalocean.com/community/tutorials/how-to-install-go-on-debian-10

# Interpreter Languages
1. Python
2. PHP
3. Ruby

## Install PHP, Ruby, Python

### Bash Setting for Pyenv, Phpenv and Rbenv:

```sh
export PATH="$HOME/.pyenv/bin:$HOME/.phpenv/bin:$HOME/.rbenv/bin:$PATH"
eval "$(phpenv init -)"
eval "$(rbenv init -)"
eval "$(pyenv init --path)"
eval "$(pyenv virtualenv-init -)"
```

#### instal dependencies of PHP

install some dependencies
```sh
sudo apt install libcurl4-openssl-dev
sudo apt install -y libjpeg-dev
sudo apt install libonig-dev (https://www.limstash.com/en/articles/202002/1539)
sudo apt-get install php-tidy
sudo apt-get install libzip-dev
```
problem: cannot find libtidy; solution: install html-tidy    
source: https://askubuntu.com/questions/823258/how-to-install-updated-version-of-html-tidy
```sh
wget https://github.com/htacg/tidy-html5/releases/download/5.4.0/tidy-5.4.0-64bit.deb
sudo dpkg -i tidy-5.4.0-64bit.deb
```

#### install laravel project
(source: https://panjeh.medium.com/how-to-install-specific-laravel-version-using-composer-f30df54632b5)

First, download the Laravel installer using Composer:

```sh
composer global require laravel/installer

```
Then
```sh
laravel new ProjectName
```

For specific version, use this command:
```sh
composer create-project laravel/laravel="5.7.*" ProjectName
```
note:    
you cannot install laravel version 5 with php 8, user php 7.x.   
other laravel version only can be installed with minimum php version.    
please do research about it.

Go to ProjectName and run
```sh
php artisan serve
```

#### install python with pyenv

install some python version

```sh
pyenv install 2.7.18
pyenv install 3.10.4
```





