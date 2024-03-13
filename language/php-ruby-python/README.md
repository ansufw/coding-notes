# Install PHP, Ruby, Python, Java

*Bash Setting for Pyenv, Phpenv and Rbenv:*

```sh
export PATH="$HOME/.pyenv/bin:$HOME/.phpenv/bin:$HOME/.rbenv/bin:$PATH"
eval "$(phpenv init -)"
eval "$(rbenv init -)"
eval "$(pyenv init --path)"
eval "$(pyenv virtualenv-init -)"
```

## PHP

referensi:
- https://stackoverflow.com/questions/34909101/how-can-i-easily-switch-between-php-versions-on-mac-osx
- https://github.com/hjbdev/pvm

### Install

>> MacOS/Linux
1. get list of program `brew search php`
2. check installed program `brew list | grep php`

>> Windows

### install dependencies of PHP

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

### install laravel project
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

## Python

#### install python with pyenv

install some python version

```sh
pyenv install 2.7.18
pyenv install 3.10.4
```

## References

- https://dev.to/micmath/manage-multiple-versions-of-php-with-homebrew-4dba
- [Managing multiple Java versions in MacOS](https://gist.github.com/gramcha/81dcec3f1e4ce8cffd7f248d3e2a42a7)
