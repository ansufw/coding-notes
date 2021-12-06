# Linux Coding Notes


## Installing fundamental software in Debian 10

- git
- vscode (snap)
- docker (snap)
- chromium (snap)
- postman

## Installing Go in Debian 10

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