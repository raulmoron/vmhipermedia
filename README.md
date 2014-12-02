# LAMP Setup based on CentOS 6.3 with Vagrant / Puppet

## Overview

LAMP environment based on CentOS, specially prepared for working in Hipermedia.

Contains:

* Apache
* MySQL
* PHP (with some useful packages)

## Installation

Clone this repo

```bash
git clone --recursive https://github.com/Konuko/vmhipermedia.git vmHipermedia
cd vmHipermedia
vagrant up
```

## Usage

* **Step 1.** **Add the `192.168.33.10` addresses in your `/etc/hosts` file**

* **Step 2.** **Open the browser**
Now, you can reach the webroot with `http://hipermedia.local`

**Some useful information:**

* The Mysql password for root is empty.
* To login into the VM type `vagrant ssh` or `ssh vagrant@192.168.33.10 -p 2222` *(password 'vagrant')*
* To halt the VM: `vagrant halt`
* To reload changes in the Vagrantfile: `vagrant reload`
* To reload changes in the puppet manifest: `vagrant provision`

If you want a graphical client to access Mysql from your machine, you can do it with a SSH tunnel:

```
SSH Host: localhost
SSH user: vagrant
SSH password: vagrant
SSH Port: 2222
MysqlHost: 127.0.0.1
Username: root
Password: #empty#
```
*There is no password, do not type "empty" :)*

You'll have two shared folders inside `shared` folder on project root:

* `www`: Your web DocumentRoot. You'll find `sifo` folder inside too.
* `logs`: Logs from Apache and MySQL will be stored here.

This two folders will be mapped on root (`/`) folder on your guest Virtual Machine with full permissions (777).

## Credits

We started this project inspireds by the [pdaether repository](https://github.com/pdaether/LAMP-CentOS-with-Vagrant) on GitHub,
although this project has been completely rewritten and adds more stuff. Almost all modules are from [Puppet Labs](http://puppetlabs.com/).