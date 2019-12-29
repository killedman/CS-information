# 安装docker

参考 https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-using-the-repository 在ubuntu上安装docker-ce



## 建立 docker 用户组，添加用户到docker组

默认情况下,docker命令会使用 Unix socket 与 Docker 引擎通讯。而只有root
用户和docker组的用户才可以访问 Docker 引擎的 Unix socket。出于安全考虑,一般 Linux 系统上不会直接使用root用户。因此,更好地做法是将需要使用docker的用户加入docker用户组。

建立docker组:

```shell
$ sudo groupadd docker
```



将当前用户加入docker组:

```shell
$ sudo usermod -aG docker $USER
```

退出当前终端并重新登录,进行测试。

对于ubuntu系统，需要注销当前用户，重新登录，否则需要在每个终端中先执行以下命令：

```shell
newgrp docker
```

此时执行docker image ls等命令不需要再添加sudo，可以直接执行了