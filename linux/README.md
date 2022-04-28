# Linux Coding Notes

## Basic Command for Server Linux

### copying file

`cp filename destination`

### moving (or rename) file

`mv filename destination/new_filename`

### login ssh

`ssh username@public_ip`

### setting firewall rule

- open ufw connection `ufw allow OpenSSH`
- enable `ufw enable`
- check status `ufw status`
- allow web server `sudo ufw allow www` or `sudo ufw allow 80/tcp`
- allow https `sudo ufw allow https`
- allow custom port `sudo ufw allow 2222/tcp` or `sudo ufw allow 2222/udp`
- add rule block certain ip address `sudo ufw deny from 10.1.1.1`
- add rule block certain ip address to access certain port `sudo ufw deny from 10.1.1.1 to any port 22`
- allow ip from paticular ip address `sudo ufw allow from 10.2.2.2 to any port 22`. be careful it only allow access ip address from 10.2.2.2 and no one else
- allow ip to access mySql `sudo ufw allow from 10.1.1.0/24 to any port 3306`
- delete rule by add number in status `sudo ufw status numbered` then `sudo ufw delete 3`

#### check port firewall

- port scanning (run this from your local) `sudo nmap -sS ip_address`
- now try to disable firewall `sudo ufw disable`, now you will see more port can be exposed by running agein `sudo nmap -sS ip_address`

### setting hostname

- to see your current hostname `sudo cat /etc/hostname`, the default host name is localhost.
- to see complete hostname data `sudo hostnamectl`
- to modif hostname `sudo hostnamectl set-hostname newhostname`

### setting timezone

- to know date and timezone run `date`
- to set timezone `sudo dpkg-reconfigure tzdata`

### install usefull tools

- run `who` to know who is online and `w` for detail data
- nethogs to see sent receive data `sudo intall nethogs`
- ip traffic monitor -> `sudo apt search iptraf` then `sudo apt install iptraf-ng` then run `sudo iptraf-ng`

### install web server

- install apache `sudo apt install apache2`
- check status `sudo systemctl status apache2`

### setting user

- add user
  `sudo adduser new_username`
- enable user to use sudo as root level
  `usermod -aG sudo new_username`
- change user
  `su - new_username`
- delete user
  `sudo userdel new_username`
- change to root
  `sudo su`
- change owner of the file
  `chown newowner:newoner namefile.txt`

### add ssh-key to ubuntu server

- crete key-gen in the terminal using command`ssh-keygen -t rsa`
- the default keygen will be stored in `/Users/username/.ssh/id_rsa`
- to open it use command `cat id_rsa.pub`
- add ssh key to server by running `ssh-copy-id username@public_ip`
- config ssh
  1. go to /etc/ssh
  2. backup config file `cp sshd_config sshd_config.dist`
  3. open `sshd_config` using `vi` or other text editor
  4. set `PasswordAuthentication` and `PermitRootLogin` to `no` and `MaxAuthTries` to `3`

### install fail2ban

- before install any software run `sudo apt update`
- then `sudo install fail2ban`
- start it by `sudo systemctl start fail2ban`
- set system start automatically when system restart `sudo systemctl enable fail2ban`
- go to `cd /etc/fail2ban/` and create `sudo vi jail.local` put these settings

```
[sshd]
enable = true
port = 22
filter = sshd
logpath = /var/log/auth.log
maxretry = 3
```

- restrat to apply configuration `sudo systemctl restart fail2ban`
- you can take a look `jail.conf` but your setting should go to `jail.local`

### File transfer

- using copying commmand `scp path/to/filename username@publicip:path/to/destination`
- using secure ftp `sftp username@publicip`

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

## list of software for works

- git
- vscode (snap)
- chromium (snap)
- docker
- postman
- chrome
- flameshot (snap)
- SSR (SimpleScreenRecorder)
- yEd graph editor
- Geany
- Vidyard (installed on Chrome)

### git installation

```sh
sudo apt update
sudo apt install git
```

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
