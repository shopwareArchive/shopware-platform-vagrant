# DEPRECATED

This repository is no longer maintained and therefor deprecated.

Please consider using [dockware.io](https://dockware.io/getstarted) if you want to setup a development environment for Shopware.
This also works great with Windows (including WSL2).

Feel free to use this repository as a baseline for setting up your own Shopware development environment with Vagrant and Ansible but keep in mind that it might be an old baseline.

Thank you for your understanding!


---


Shopware Development build with Vagrant
=======================================

## Table of contents
1. [Vagrant VM](#vagrant-vm)
2. [Installation](#installation)
3. [Usage](#usage)
4. [Shopware Dev setup](#shopware-dev-setup)
5. [Useful vagrant commands](#useful-vagrant-commands)
6. [Connecting your IDE](#connecting-your-ide)


## Vagrant VM
If using docker is not an option for you, vagrant is another great technology to quickly get a local Shopware up and running.

Other than with the docker or local setup, with vagrant you will have a complete seperate server on your machine.

Because of technical reasons, the vagrant machine acts like a remote web server, so with this setup, you'll develop your code on your PC like and then you upload/synchronize it to the vagrant machine.

For this, the vagrant machine supports SCP/SSH, which is integrated in Editors like PHPStorm or Visual Studio Code.


## Installation
You need VirtualBox, Vagrant (min. Version 2.0) and Git installed locally on your machine.
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Vagrant](https://www.vagrantup.com/downloads.html)
- [Git](https://git-scm.com)
- [Vagrant Hostsupdater](https://github.com/cogitatio/vagrant-hostsupdater) (optional)

The IP address `192.168.33.10` is used by the vagrant box, so it must not be in use in the network already. If this is not possible, you manually have to change the IP address in the `Vagrantfile` you'll clone in the next step.


## Usage
This section explains the basic setup of the virtual machine, as well as an advanced setup, using a reverse proxy and SSL.

### Basic setup
Start by cloning this repository to your local machine
    
    $ git clone git@github.com:shopwareLabs/shopware-platform-vagrant.git
    $ cd shopware-platform-vagrant

Boot up the virtual machine by executing `vagrant up` 
    
    $ vagrant up

The first boot takes a while due to box download and ansible provisioning. Feel free to grab a drink.

After the process completes your virtual machine will be up an running with your development environment ready to use. 

The storefront will be available at [http://192.168.33.10/](http://192.168.33.10/).

The administration will be available at [http://192.168.33.10/admin](http://192.168.33.10/admin). The default credentials are `admin/shopware`.

Credentials for ssh access are `vagrant/vagrant`.

You connect via `vagrant ssh` or use credentials and ssh with the following command (make sure ssh known_hosts is correct):

    $ ssh vagrant@192.168.33.10

### Shopware versions

By editing the `ansible/vars/all.yml` file you are able to set the `shopware_version` variable. This variable references the branch
name of the devlopment template which is used to build the vagrant VM. 
This can be the literal string HEAD, a branch name or a tag name of this repository: https://github.com/shopware/development

By default this variable is set to the `trunk` branch.
To use a specific version you can set the corresponding git tag: `v6.2.2`

In it's current state this setup cannot be used to update a running shopware instance via `shopware_version` variable and re-provisioning
via vagrant. 

### Advanced setup
If you would like to access the Shopware instance using a hostname, rather than the IP address,
you can enable the reverse proxy and - if you like - SSL encryption.

Both proxy and SSL can be enabled by editing the `ansible/vars/all.yml`. In this file,
you will find the following options and be able to modify them accordingly.

| Variable       | Type             | Default               | Description                                                            |
|----------------|------------------|-----------------------|------------------------------------------------------------------------|
| proxy_enabled  | Boolean (yes/no) | no                    | Enables the installation of nginx as a reverse proxy                   |
| proxy_hostname | Hostname         | "shopware.local"      | Defines the hostname that will be used to access the Shopware instance |
| proxy_ssl      | Boolean (yes/no) | no                    | Enables SSL                                                            |

Please notice that you will have to modify your hosts file or use the Vagrant Hostsupdater plugin,
when using a reverse proxy setup.

Given the hosts entry is set, you can access the Shopware instance via `https://<proxy_hostname>`, whereas
`<proxy_hostname>` is a placeholder for the configured hostname (shopware.local per default).

---

## Shopware Dev setup

For more info on the Shopware dev setup visit [our Shopware platform docs](https://docs.shopware.com/en/shopware-platform-dev-en) or take a look at the [vagrant guide](https://docs.shopware.com/en/shopware-platform-dev-en/getting-started/system-installation-guides/vagrant?category=shopware-platform-dev-en/getting-started/system-installation-guides)

---

## Useful vagrant commands 

Connect to your VM via ssh
    
    $ vagrant ssh 

(Re-)provision your environment

    $ vagrant provision

Delete your VM 

    $ vagrant destroy

Status of your VM

    $ vagrant status

---

## Connecting your IDE

The vagrant box fully encapsulates the whole platform with all its sources. So the development process works just like with any other foreign system. The machine supports SCP with the following credentials.

| Key       | Setting           |
|---        |---                |
| Host      | 192.168.33.10     |
| User      | vagrant           |
| Password  | vagrant           |
| Path      | ~/shopware-dev    |
