# Linux Coding Notes

## Basic Command

### copying file

`cp filename destination`

### moving (or rename) file

`mv filename destination/new_filename`

### login ssh

`ssh username@public_ip`

### add ssh-key to ubuntu server

crete key-gen in the terminal using command`ssh-keygen -t rsa`

the default keygen will be stored in `/Users/username/.ssh/id_rsa`

to open it use command `cat id_rsa.pub`

add ssh key to server by running `ssh-copy-id username@public_ip`

config ssh

1. go to /etc/ssh
2. backup config file `cp sshd_config sshd_config.dist`
3. open `sshd_config` using `vi` or other text editor
4. set `PasswordAuthentication` and `PermitRootLogin` to `no` and `MaxAuthTries` to `3`

## Setting BunsenLabs (Debian 10)

BunsenLabs Linux is a distribution offering a light-weight and easily customizable Openbox desktop.

### Setting menu

go to `menu` > `Preferences` > `jgmenu` > `Edit Menu Content`

in the last of line in file `prepend.csv`, add the following lines

```csv
^tag(apps)
Back,^back()
Chromium, /snap/bin/chromium
Postman, postman
Code, /snap/bin/code
MySql-Workbench, /snap/bin/mysql-workbench-community
```

## Installing fundamental software in Debian 10

- git
- vscode (snap)
- chromium (snap)
- docker
- postman
- chrome

### git installation

```sh
sudo apt update
sudo apt install git
```

### Installing Go in Debian 10

execute these following lines on the terminal

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

### Install chrome

download google chrome package

```sh
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

install google chrome

```sh
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

### Install XDM

download xdm from here [github](https://github.com/subhra74/xdm/releases) then extract with command `tar xvf <tar file name>`. Run with `sudo ./install.sh`. After installation done then start XDM from start menu.
