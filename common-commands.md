# 系统管理常用命令整理



ls -RF dir/* 递归列出目录下及子目录下文件

## rpm包管理相关

rpm -qf 后面跟文件名称查找该文件属于哪个rpm包
rpm -ql 后面跟已安装的包查询该包中的文件，结合grep过滤
rpm -qpR 后面跟rpm包名，查看这个包的依赖
rpm -qa |grep 跟关键词查找特定的包是否安装
rpm -ivh 后面跟rpm包进行包安装
rpm -e 后面跟rpm -qa命令查询出来的包名进行卸载

