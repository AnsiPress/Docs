AnsiPress Documentation

## Quick Setup
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2FAnsiPress%2FDocs.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2FAnsiPress%2FDocs?ref=badge_shield)


AnsiPress is based on Ansible. So AnsiPress can operate from any system where Ansible can be installed.

### Prerequisites

* SSH Setup
* Ansible Installation
* Ansible Hosts File

#### SSH Setup

In order to make AnsiPress works, we should be able to connect to remote server via `ssh hostname`

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

Now you are ready to run AnsiPress commands

### Commands

AnsiPress commands currently use Ansible base commands. You will see  easy to run, wrapper commands very soon.

##### Base command

```
ansible-playbook
```

##### Parameters

* -i specifies the inventory hosts file to run ansible tasks on.
* --extra-vars specifies the variables and its values required while running the ansible tasks

##### Variables

* **username**   - This  variable will create a separate linux user which will have access to the particular website you are going to create. If you want to use the same user to host multiple website you can use the same user name everytime you run the command

* **website\_name -  **This variable specifies the domain name of the website. just like `example.com`

* **website\_type - **This variable setup the configuration for the website according to the type specified among

  * html - specifies set of tasks to run configure a website that can serve static contents only
  * php -  specifies set of tasks to run that configures a web app/site that requires php and can run without database.
  * mysql - specifies set of tasks to run that configures a web app/site that requires php and mysql database.
  * wp - specifies set of tasks to run that configures a wordpress website.
  * w3tc - specifies set of tasks to run that configures a wordpress website and install w3 total cache plugin for cacheing purpose.
  * wpfc - specifies set of tasks to run that configures wordpress website and setup fastcgi cache configuration, generally required for high traffic websites.

### Example commands to create site

#### HTML

```
$ ansible-playbook -i hosts setup.yml --extra-vars="username=exampleuser website_name=html.com website_type=html"
```

#### PHP

```
$ ansible-playbook -i hosts setup.yml --extra-vars="username=exampleuser website_name=php.com website_type=php"
```

#### MySQL

```
$ ansible-playbook -i hosts setup.yml --extra-vars="username=exampleuser website_name=mysql.com website_type=mysql"
```

### WordPress Sites

#### WP

```
$ ansible-playbook -i hosts setup.yml --extra-vars="username=exampleuser website_name=wp.com website_type=wp"
```

#### W3TC

```
$ ansible-playbook -i hosts setup.yml --extra-vars="username=exampleuser website_name=w3tc.com website_type=w3tc"
```

#### WPFC

```
$ ansible-playbook -i hosts setup.yml --extra-vars="username=exampleuser website_name=wpfc.com website_type=wpfc"
```

## Purge FastCGI Cache

```
Clean Homepage: http://example.com/purge
Clean Hello World Post: http://example.com/purge/hello-world
Clean All NGINX FastCGI Cache: http://example.com/purge.php 

```

## Google Pagespeed

```
Pagespeed stats:  http://example.com/ngx_pagespeed_statistics

Tempp Disable Pagespeed: http://example.com/?PageSpeed=off

Purge File From Pagespeed cache: http://exmple.com/pagespeed_admin/cache?purge=/path/file.ext
```

## Lets Encrypt

```
$ sudo certbot --nginx certonly -d example.com -d www.example.com
$ vim /home/exampleuser/vhosts/example.com/conf/ssl.conf
listen 80;
listen 443 ssl http2;
ssl on;
ssl_certificate     /etc/letsencrypt/live/example.com/fullchain.pem;
ssl_certificate_key     /etc/letsencrypt/live/example.com/privkey.pem;

$ nginx -t && service nginx reload
```

For more details about certbot refer - [https://certbot.eff.org/\#ubuntuxenial-nginx](https://certbot.eff.org/#ubuntuxenial-nginx)



## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2FAnsiPress%2FDocs.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2FAnsiPress%2FDocs?ref=badge_large)