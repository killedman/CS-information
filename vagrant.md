# install vagrant in ubuntu 18.04 LTS

## 准备

1. 安装virtualbox

## 从官网下载安装包

从vagrant官网[下载linux版本的vagrant]( https://www.vagrantup.com/downloads.html),选择Linux 64-bit，下载下来是一个zip包，解压后只有一个叫做vagrant的可执行文件。

这个步骤需要解压vagrant zip包到～/Downloads/目录下

## 安装配置

sudo mkdir -p /opt/vagrant/bin;
sudo mv ~/Downloads/vagrant /opt/vagrant/bin;
sudo ln -s /opt/vagrant/bin/vagrant /usr/bin/vagrant



以上软链接可以省去设置环境变量的步骤



## 测试

vagrant --version



## 下载box

> # [Download Vagrant box from vagrantcloud.com](https://stackoverflow.com/questions/24958110/download-vagrant-box-from-vagrantcloud-com)
>
> 
>
> *Yes, you can download virtualbox.box from*
>
> ```
> https://app.vagrantup.com/laravel/boxes/homestead/versions/6.4.0/providers/virtualbox.box
> ```
>
> *You can change the version of homestead box. Current version: 6.4.0.*
>
> *Check for the latest version here: https://app.vagrantup.com/laravel/boxes/homestead*
>
> *After downloading the box, rename it to virtualbox.box or whatever name you like.*
>
> *Don't forget to include the .box extension.*
>
> ***Add the downloaded homestead box to vagrant:***
>
> ```
> vagrant box add laravel/homestead /path/to/virtualbox.box
> ```
>
> *Change the path to where you stored your downloaded homestead box.*



首先从 https://app.vagrantup.com/boxes/search 选择需要的box，点击该box进入它自己的web页面，比如[hashicorp](https://app.vagrantup.com/hashicorp)/[precise64](https://app.vagrantup.com/hashicorp/boxes/precise64) 

we get speical  url : https://app.vagrantup.com/hashicorp/boxes/precise64/versions/1.1.0/providers/virtualbox.box

let us begin :

```shell
wget https://app.vagrantup.com/hashicorp/boxes/precise64/versions/1.1.0/providers/virtualbox.box
mv ~/Downloads/vritualbox.box ~/vagrant_test/precise64.box
vagrant box add hashicorp/precise64 ~/vagrant_test/precise64.box
```

create Vagrantfile by execute command :

```shell
vagrant init hashicorp/precise64
```

or create Vagrantfile, content as follow:

```shell
Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/precise64"
end
```

and execute:

```shell
vagrant up
```

手动下载box，并通过执行 vagrant box add命令添加的原因自动下载的太慢了；如果vagrant up命令执行时，发现没有找到box就会根据Vagrantfile的配置去下载；

execute followed commands, will ssh to defaults vm and destroy defaults vm

```shell
vagrant ssh

vagrant destroy
```

