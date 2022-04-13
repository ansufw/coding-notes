When i was child, my father give me book about visual basic.. then i continue learning Pascal when i was in senior highschool. But my bachelor and master degree was not in computer science degree. Fortunately, I married with woman that call me to back pursue my dream as computer scientist () 

Fullstack languages
1. JavaScript

Compiler Languages
1. Go
2. C++

Interpreter Languages
1. Python
2. PHP
3. Ruby

# Install PHP, Ruby, Python

## Bash Setting for Pyenv, Phpenv and Rbenv:

```sh
PATH="$HOME/.pyenv/bin:$HOME/.phpenv/bin:$HOME/.rbenv/bin:$PATH"
eval "$(phpenv init -)"
eval "$(rbenv init -)"
eval "$(pyenv init --path)"
eval "$(pyenv virtualenv-init -)"
```

### instal dependencies of PHP

install some dependencies
```
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



