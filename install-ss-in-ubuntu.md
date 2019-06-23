

# ubuntu安装shadowsocks 
## 使用pip安装ss

pip install shadowsocks

sslocal -help来查看帮助



## 配置开机自动启动ss服务

然后 sudo vim /etc/rc.local 编辑，在最下面输入 nohup bash /home/username/Documents/dl.sh>/home/username/dl.log & 保存

dl.sh的内容如下,需要替换server_ip、server_port、password：

```shell
!/bin/bash

PATH  = $PATH:/usr/local/bin/
export $PATH
sslocal -s server_ip -p server_port -l 1080 -k "password" -t 600 -m aes-256-cfb
```

-s表示服务IP, -p指的是服务端的端口，-l是本地端口默认是1080, -k 是密码（要加""）, -t超时默认300,-m是加密方法默认aes-256-cfb，

可以简单的写为：sslocal -s ip  -p  port -k "password"    #用-s -p -k这三个参数就好，其他的默认将服务端的加密方法设为aes-256-cfb。然后就可以启动代理。

## 参考:

https://www.zybuluo.com/Frankchen/note/307683

https://bwgjms.com/post/how-to-buy-justmysocks/



# iphone上如何使用ss

use app SsrConnect