# ubuntu上安装pycharm

On Ubuntu?

PyCharm is now also available as a snap package. If you’re on Ubuntu 16.04 or later, you can install PyCharm from the command line:

sudo snap install [pycharm-professional|pycharm-community] --classic

from: https://www.jetbrains.com/pycharm/download/#section=linux



执行命令： sudo snap install pycharm-community --classic  (速度太慢了，需要在网上搜索加速方法）

没有找到解决snap安装速度太慢的问题，十几k的速度，下载三百多m的安装包需要十几个小时，最后直接下载了tar.gz的安装包，解压后，运行bin目录下的sh文件后就可以使用pycharm了，将pycharm锁定在launcher，就是左边的类似于windows状态栏的地方就可以很方便的使用了。

```shell
sudo tar xzvf pycharm-community-2019.1.3.tar.gz   -C /opt/
cd /opt/pycharm-community-2019.1.3/bin;
sh pycharm.sh
```

