# CODE SNIPPETS

## install python on Debian 10
1. update system `sudo apt update && sudo apt upgrade`
2. install the required dependencies `sudo apt install build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev libsqlite3-dev wget libbz2-dev`
3. download gzippeed tarbal `wget https://www.python.org/ftp/python/3.10.*/Python-3.10.*.tgz` from official source https://www.python.org/downloads/source/
4. extract tarbal `tar -xf Python-3.10.*.tgz`
5. navigate into extracted directory `cd Python-3.10.*/` and optimize the binary and run multiple test by using `./configure --enable-optimizations`
6. build Python 3.10 from the source `make -j 4`. j flag is used to speed up the system. `nproc` command shows your system core
7. when make is complete, proceed and install python 3.10 on Debian `sudo make altinstall`.  altinstall flag is used to maintain the default Python binary path in /usr/bin/python
8. verify your installation `python3.10 --version` or `python3.10 -VV`

source: https://computingforgeeks.com/how-to-install-python-on-debian-linux/

## install python module on Debian 10
1. `sudo apt install python3-pip`
2. `sudo pip3.10 install module-name` for example `sudo pip3,10 install beautifulsoup4`

## check installed python
- check location `ls -ls /usr/bin/python*` or `whereis python` 
- to know path installed python `which python` or `which python3`

## create new env
1. create project directory `mkdir pythonapp && cd pythonapp`
2. create virtual environment `python3.9 -m venv pythonapp_env`, where `pythonapp_env` is name of environment for the project
3. run `source pythonapp-env/bin/activate` to activate the environment
4. run `deactivate` to deactivate


## python-golang comparison

| python | golang |
|--------|-------|
| _venv_ | _go modules_ |
| _requirement.txt_ | _go.mod_ |
| `pip install -r requirement.txt` | `go mod tidy` |
| `pip freeze > requirement.txt` | `go mod init project_name` |
 
