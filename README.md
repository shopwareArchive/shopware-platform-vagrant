Shopware Development build with Vagrant
=======================================

## Installation
You need VirtualBox and Vagrant (min. Version 2.0) installed locally on your machine.
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Vagrant](https://www.vagrantup.com/downloads.html)

## Usage

Clone this repository to your local machine
    
    $ git clone https://stash.shopware.com/scm/tool/vagrant-dev-box-next.git
    $ cd vagrant-dev-box-next

Boot up the virtual machine using Vagrant
    
    $ vagrant up

The first boot may take a while due to box download and ansible provisioning. Feel free to grab a drink.

After the process completes your virtual machine will be up an running with your development environment ready to use. 

The storefront will be available at [http://192.168.33.10/](http://192.168.33.10/)

The administration will be available at [http://192.168.33.10/admin](http://192.168.33.10/admin)

---

## Shopware Dev setup

For more info on the Shopware Dev Setup visit [Shopware Dev Setup - Getting started](https://docs.shopware.com/en/shopware-platform-en/getting-started/dev-setup?category=shopware-platform-en/getting-started)

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
