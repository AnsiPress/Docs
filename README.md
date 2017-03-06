AnsiPress Documentation

## Quick Setup

AnsiPress is based on Ansible. So AnsiPress can operate from any system where Ansible can be installed.

### Prerequisites

* SSH Setup
* Ansible Installation
* Ansible Hosts File

#### SSH Setup

In order to make AnsiPress works, We have to able remote server via `ssh hostname`

```
$ vim ~/.ssh/config
Host AnsiPress.local
  user root
  port 22
  hostname 192.168.33.16
```

Test SSH Connection

`$ ssh AnsiPress.local`

#### Install Ansible

Ansible Installed on the machine\(controller\) where from you will be managing your servers.  

This can be your local system or your server where you want to setup your stack.

#### Ubuntu

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
$ git clone https://github.com/AnsiPress/AnsiPress.git
```

#### Setup Ansible hosts file

```
$ cd AnsiPress && vim hosts
[AnsiPress]
AnsiPress.local
```



