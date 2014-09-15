# 容器
##启动容器
所需要的命令主要为`docker run`

例如，下面的命令输出一个"Hello World"，之后终止容器。
```
$ sudo docker run ubuntu:14.04 /bin/echo 'Hello world'
Hello world
```

下面的命令则启动一个bash终端，可以让用户进行交互。
```
$ sudo docker run -t -i ubuntu:14.04 /bin/bash
root@af8bae53bdd3:/#
```
其中，`-t`选项让Docker分配一个伪终端（pseudo-tty）并绑定到容器的标准输入上， `-i`则让容器的标准输入保持打开。

在交互模式下，用户可以通过所创建的终端来输入命令，例如
```
root@af8bae53bdd3:/# pwd
/
root@af8bae53bdd3:/# ls
bin boot dev etc home lib lib64 media mnt opt proc root run sbin srv sys tmp usr var
```

当利用`docker run`来创建容器时，Docker在后台运行的标准操作包括：

* 检查本地是否存在指定的镜像，不存在就从公有仓库下载
* 利用镜像创建并启动一个容器
* 分配一个文件系统，并在只读的镜像层外面挂载一层可读写层
* 从宿主主机配置的网桥接口中桥接一个虚拟接口到容器中去
* 从地址池配置一个ip地址给容器
* 执行用户指定的应用程序

##终止容器

当Docker容器中指定的应用终结时，容器也自动终止。
例如用户通过`exit`命令或`Ctrl+d`来退出终端时，所创建的容器立刻终止。