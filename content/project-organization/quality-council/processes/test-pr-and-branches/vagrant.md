---
title: Using the Vagrant virtual machine
aliases:
  - /maintainers-guide/test-pr-and-branches/vagrant/
---

{{% notice warning %}}
**Vagrant repository is no longer updated.** 

To test the PrestaShop pull requests, we recommend using the [Docker environment](https://devdocs.prestashop-project.org/8/contribute/contribute-pull-requests/contribute_using_docker/) or local installation.
{{% /notice %}}

# Using the Vagrant virtual machine

We recommend using our virtual machine to quickly get a testing environment in place.

## Requirements

This is what you need to run this project:

- [Vagrant](https://www.vagrantup.com/downloads.html)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

If you're using Windows, we recommend you to download [Git bash](https://git-scm.com/downloads) and execute all commands under this shell.

## What is installed

- Debian 10 Buster
- Git
- Apache 2.4
- Multiple PHP versions (7.1, 7.2, 7.3, 7.4)
- MariaDB 10
- NodeJS

## Getting started


First, you must clone the repository [https://github.com/PrestaShop/vagrant](https://github.com/PrestaShop/vagrant).

Second, execute the script `run.sh` (or `run.bat` if you're under Windows) and follow instructions.

Most of the time, there is a prompt asking for a network interface, remember it's the communication between the virtual machine and the network card.

{{< figure src="../img/vagrant/run-script.png" alt="Running the run.sh script" >}}

The first installation will take a while, because it needs to download the vagrant box, installs all needed packages and configures the system to make it compatible with PrestaShop.
{{< figure src="../img/vagrant/script-ended-successful.png" alt="Script running successfuly" >}}

Then, visit [http://192.168.42.42/prestashop](http://192.168.42.42/prestashop).

phpMyAdmin is also available at [http://192.168.42.42/phpmyadmin](http://192.168.42.42/phpmyadmin).

### Environments

#### Available PHP versions

- 7.1
- 7.2
- 7.3
- 7.4

{{% notice tip %}}
Be aware that some PrestaShop versions are not compatible with all the above environments. See [System requirements]({{< devdocs "basics/installation/system-requirements" >}}) to find out which version is compatible with which PHP version.
{{% /notice %}}


#### PrestaShop

- Username: `demo@prestashop.com`
- Password: `prestashop_demo`

#### MySQL

phpMyAdmin is available at [http://192.168.42.42/phpmyadmin](http://192.168.42.42/phpmyadmin).

- MySQL Host: `127.0.0.1`
- Database name: `prestashop`
- Username: `prestashop`
- Password: `prestashop`
- Port: `3306`

#### SSH

You can login into the virtual machine with `vagrant ssh`


### Troubleshooting

If something went wrong during the installation, the error is displayed explaining which command is failing.

* Invalid branch name:

<img src="../img/vagrant/build-failed.png" alt="Invalid git branch name" class="mx-lg-4" style="max-width: 700px">

* Invalid PHP version:

<img src="../img/vagrant/invalid-php-version.png" alt="Invalid PHP version" class="mx-lg-4" style="max-width: 700px">
