# 系统管理常用命令整理

1. ls -RF dir/* 递归列出目录下及子目录下文件

## rpm包管理相关

1. rpm -qf 后面跟文件名称查找该文件属于哪个rpm包
2. rpm -ql 后面跟已安装的包查询该包中的文件，结合grep过滤
3. rpm -qpR 后面跟rpm包名，查看这个包的依赖
4. rpm -qa |grep 跟关键词查找特定的包是否安装
5. rpm -ivh 后面跟rpm包进行包安装
6. rpm -e 后面跟rpm -qa命令查询出来的包名进行卸载

## 在ubuntu上安装git gui客户端GitKraken

参考： https://www.cnblogs.com/EasonJim/p/7209135.html

## ubuntu上安装wine和notepad++

 https://www.configserverfirewall.com/ubuntu-linux/install-wine-ubuntu-16-04/

## How to uninstall pip2 


If you installed pip like this:

 - sudo apt install python-pip
 - sudo apt install python3-pip

Uninstall them like this:

 - sudo apt remove python-pip
 - sudo apt remove python3-pip

## How to install Pip3 & Django on Ubuntu 18.04 / Ubuntu 16.04 LTS

sudo apt -y install python3-pip
