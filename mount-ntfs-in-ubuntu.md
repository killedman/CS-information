## ubuntu下挂载ntfs盘

sudo mount -t "ntfs" -o /dev/sda6 /media/dreamsn/wendang/
sudo mount -t "ntfs" -o /dev/sda5 /media/dreamsn/ruanjian

以上挂载方式为只读模式，使用ntfs-3g方式则可以实现可读可写

sudo mount -t ntfs-3g  /dev/sda6 /media/dreamsn/wendang/
sudo mount -t ntfs-3g /dev/sda5 /media/dreamsn/ruanjian

执行sudo mount -t ntfs-3g  /dev/sda6 /media/dreamsn/wendang/（通过指定ntfs-3g而不是ntfs解决挂载的磁盘只读不能写的问题）挂载ntfs分区报错Metadata kept in Windows cache, refused to mount的解决方法：先确保分区没有挂载；修复挂载错误的相应的分区,如提示中的/dev/sda5，输入：sudo ntfsfix /dev/sda5

参考： https://www.cnblogs.com/imqsl/p/6567917.html

