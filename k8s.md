# 安装minikube和kubectl，启用单节点kubernetes集群



https://kubernetes.io/docs/setup/learning-environment/minikube/

下载minikube和kubectl后，添加可执行权限，新建一个目录/opt/k8s/，添加软链接到/usr/local/bin

```shell
ln -s /opt/k8s/minikube /usr/local/bin/minikube
ln -s /opt/k8s/kubectl /usr/local/bin/kubectl
```

执行minikube start失败：

<img src="/home/dreamsn/Pictures/Screenshot from 2019-07-28 17-27-25.png" />

from [her]( https://github.com/kubernetes/minikube/issues/4035) i find the result. as follow:

> Thanks for the bug report!
>
> I believe that the root cause here is we're trying to download too  much (7 Linux images simultaneously!), and some networks don't deal with  this well.
>
> This should eventually unhang.
>
> You can test my root cause theory by using:
>
> ```
> minikube start --cache-images=false
> ```
>
> This will end up serializing the image downloads.

以上的方法开始下载几秒后就不动了，卡住了；

接着从[这里](https://qii404.me/2018/01/06/minukube.html)我找到了一个方法，让curl、wget也走代理

> 如果你下载工具时提示下载错误，基本上就是因为GFW，所以如果你有本地ss能够科学上网的话，可以在终端里执行下面命令，让 curl wget等命令也会走代理，加快下载
>
> ```
> export http_proxy='socks5:127.0.0.1:1080'
> ```
>
> 有个坑，执行完以后访问 127.0.0.1 也是会走代理，这时候当然要换一个tab访问即可。

成功执行minikube start启动一个kubernetes集群的过程如下：

![](/home/dreamsn/Pictures/Screenshot from 2019-07-29 11-22-50.png)

执行kubectl cluster-info查看集群状态

![](/home/dreamsn/Pictures/Screenshot from 2019-07-29 16-35-21.png)



