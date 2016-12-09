# vagrant-mint
Mint cinnamon + LAMP Ansible playbook
### Setting up a new dev box:
* Install Vagrant (http://www.vagrantup.com/downloads.html)
* Install Oracle Virtualbox 5.0 platform package & Extension Pack (https://www.virtualbox.org/wiki/Downloads)
* Open a Windows/DOS command line terminal and enter the following commands
```
	> vagrant plugin install vagrant-persistent-storage
	> vagrant box add artem-sidorenko/mint-18.0-cinnamon
    > cd C:\path\to\vagrant-mint
	> vagrant up
```

### Accessing the box:
A few reasons why you may find convenient logging in and developing as www-data (apache user):
* The /var/www folder can be mapped as a Windows network drive (see below for instructions)
* The /var/www folder persists even after vagrant destroy (persistent storage plugin)
* Avoid ownership and permission conflicts with apache
```
username: www-data
password: www-data
```
Provisioning can take a few minutes, when complete write down the ip address shown for
```
	enp0s8 -> inet addr
```

### Map Samba drive:
Samba is also included to allow use of your favorite Windows IDE
	On Windows Explorer right click on 'This PC'
> Map network drive -> \\xx.xx.xx.xx\www-data<br>
> Where xx.xx.xx.xx = your.vagrant.ip<br>
> User/pwd: www-data/www-data<br>
> The xx.xx.xx.xx ip should be on screen once 'vagrant up' has completed. Look under ```enp0s8 -> inet addr```

Based on the **artem-sidorenko/mint-18.0-cinnamon** vagrant image.