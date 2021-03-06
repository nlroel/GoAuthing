# GoAuthing

## Replace auth.tsinghua.com to gw.buaa.edu.cn

[![Build Status](https://travis-ci.org/z4yx/GoAuthing.svg?branch=master)](https://travis-ci.org/z4yx/GoAuthing)
![GPLv3](https://img.shields.io/badge/license-GPLv3-blue.svg)

A commandline Tunet (gw.buaa.edu.cn, BUAA-IPv4) authentication tool.

## Download Binary

Download prebuilt binaries from https://github.com/z4yx/GoAuthing/releases  
Or https://mirrors.tuna.tsinghua.edu.cn/github-release/z4yx/GoAuthing/

## Usage

Simply try `./auth-thu`, then enter your user name and password.

```
NAME:
   auth-thu - Authenticating utility for Buaa

USAGE:
   auth-thu [options]
   auth-thu [options] auth [auth_options]
   auth-thu [options] login
   auth-thu [options] logout

VERSION:

   1.4

AUTHORS:
  Yuxiang Zhang <yuxiang.zhang@tuna.tsinghua.edu.cn>
  Nogeek <ritou11@gmail.com>

COMMANDS:
     auth    (default) Auth via gw.buaa.edu.cn
       OPTIONS:
           --ip value      authenticating for specified IP address
           --no-check, -n  skip online checking, always send login request
           --logout, -o    log out of the online account
           --ipv6, -6      authenticating for IPv6 (gw.buaa.edu.cn)
           --host value    use customized hostname of srun4000
           --insecure      use http instead of https
     login   Login via net.tsinghua
     logout  Logout via net.tsinghua

GLOBAL OPTIONS:
   --username name, -u name          your TUNET account name
   --password password, -p password  your TUNET password
   --config-file path, -c path       path to your config file, default ~/.auth-thu
   --hook-success value              command line to be executed in shell after successful login/out
   --debug                           print debug messages
   --help, -h                        print the help
   --version, -v                     print the version
```

Write a config file to store your username & password or other options in the following format.
The default location of config file is `~/.auth-thu`.

```
{
  "username": "your-username",
  "password": "your-password",
  "host": "gw.buaa.edu.cn",
  "ip": "10.xxx.xx.xx",
  "debug": false,
  "useV6": false,
  "noCheck": false,
  "insecure": false
}
```

To configure automatic authentication on systemd based Linux distro, take a look at `docs` folder. Just modify the path in configure files, then copy them to `/etc/systemd/system` folder.

## Build

Requires Go 1.11 or above

```
export GO111MODULE=on
go build -o auth-thu github.com/z4yx/GoAuthing/cli
```

## Acknowledgments

This project was inspired by the following projects:

- https://github.com/jiegec/auth-tsinghua
- https://github.com/Berrysoft/ClassLibrary
