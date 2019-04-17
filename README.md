Shopware Development build with Vagrant
=======================================

## Installation
You need VirtualBox and Vagrant (min. Version 2.0) installed locally on your machine.
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Vagrant](https://www.vagrantup.com/downloads.html)

## Usage

Clone this repository to your local machine
    
    $ git clone git@github.com:shopwareLabs/shopware-platform-vagrant.git
    $ cd shopware-platform-vagrant

Boot up the virtual machine using Vagrant
    
    $ vagrant up

The first boot may take a while due to box download and ansible provisioning. Feel free to grab a drink.

After the process completes your virtual machine will be up an running with your development environment ready to use. 

The storefront will be available at [http://192.168.33.10/](http://192.168.33.10/)

The administration will be available at [http://192.168.33.10/admin](http://192.168.33.10/admin)

Credentials for ssh access are vagrant/vagrant 

You can connect via `vagrant ssh` or `ssh -p 2222 vagrant@127.0.0.1` 

---

## Shopware Dev setup

For more info on the Shopware dev setup visit [our docs](https://docs.shopware.com/en/shopware-platform-dev-en/getting-started/installation-guide)

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
