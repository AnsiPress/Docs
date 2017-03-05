# AnsiPress Documentation

## Quick Setup

AnsiPress is based on Ansible. So AnsiPress can operate from any system where Ansible can be installed.

### Prerequisites

Ansible Installed on the machine\(controller\) where from you will be managing your servers.  This can be your local system or your server where you want to setup your stack.

#### Install Ansible  \(on Controller Machine\)

##### Ubuntu

```
$ sudo apt-get install software-properties-common
$ sudo apt-add-repository ppa:ansible/ansible
$ sudo apt-get update
$ sudo apt-get install ansible
```

##### CentOS

```
$ sudo yum install epel-release
$ sudo yum install ansible
```

##### MAC OSX

```
$ brew install ansible
```

#### Install AnsiPress Beta Version

```
$ git clone -b 'v0.1.0-beta' --single-branch --depth 1 https://github.com/AnsiPress/AnsiPress.git
```

#### Setup Ansible hosts file

```
$ cd AnsiPress
```

Setup hosts  file according to following format

```
$ vim hosts
[AnsiPress]
AnsiPress.local
```



