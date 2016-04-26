# dosh

Docker in the Shell

shell command for isolated, docker container environments.


### Requirements

Linux or Mac OS X

Docker >= 1.2.0

Bash >= 3.0


### Install dosh

Download dosh, and place in your $PATH

```bash
$ git clone https://github.com/luuvish/dosh
$ cp dosh/dosh /path/to/your/bin
$ export PATH=$PATH:/path/to/your/bin
$ dosh
```


### Run dosh

Mount your current directory and execute shell command in docker

```bash
$ pwd
/Users/luuvish/Documents/dosh.git
$ uname -s
Darwin
$ ls
LICENSE README.md dosh
$ dosh
/Users/luuvish/Documents/dosh.git $ ls
LICENSE README.md dosh
/Users/luuvish/Documents/dosh.git $ uname -s
Linux
/Users/luuvish/Documents/dosh.git $ exit
$
```

Run ubuntu 14.04 docker base container

```bash
$ dosh ubuntu:14.04 uname -s
Linux
$ dosh ubuntu:14.04 which dash
/bin/bash
```


### Extend shell command container

Create a docker container that include make command.

```
# Dockerfile
FROM ubuntu:14.04
RUN apt-get update && apt-get install -y make
```

Build a docker image

```
$ docker build -t make .
```

Run dosh

```
$ dosh make make --version
GNU Make 3.81
Copyright (C) 2006 ...
```
