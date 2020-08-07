# docker 常用命令
## Docker version 命令  

docker version :显示 Docker 版本信息。  

**语法**
>docker version [OPTIONS]  

**OPTIONS说明：**
-f :指定返回值的模板文件。  

**实例** <br>
显示 Docker 版本信息。  

>$ docker version <br>
>Client: <br>
>>Version:      1.7.1 <br>
 API version:  1.19 <br>
 Go version:   go1.4.2 <br>
 Git commit:   0a8c2e3/1.7.1 <br>
 OS/Arch:      linux/amd64 <br>  

>Server: <br>
>>Version:      1.7.1 <br>
 API version:  1.19 <br>
 Go version:   go1.4.2 <br>
 Git commit:   0a8c2e3/1.7.1 <br>
 OS/Arch:      linux/amd64 <br>

## Docker info 命令  

docker info : 显示 Docker 系统信息，包括镜像和容器数。  

**语法**
>docker info [OPTIONS]  

**实例**<br>
查看docker系统信息。
>$ docker info <br>
Containers: 2 <br>
Images: 12 <br>
Storage Driver: devicemapper <br>
 Pool Name: docker-253:3-2359672-pool <br>
 Pool Blocksize: 65.54 kB <br>
 Backing Filesystem: extfs <br>
 Data file: /dev/loop0 <br>
 Metadata file: /dev/loop1 <br>
 Library Version: 1.02.117-RHEL6 (2016-12-13) <br>
Execution Driver: native-0.2 <br>
Logging Driver: json-file <br>
Kernel Version: 3.10.105-1.el6.elrepo.x86_64 <br>
Operating System: centos 6 <br>
CPUs: 4 <br>
Total Memory: 5.196 GiB <br>
Name: panxiang <br>
ID: ZM5K:TXHR:JX2J:2HT5:23PV:TFU2:SV7H:7Z5P:S6DH:ZWZ7:MZCZ:CKKX

## Docker run 命令

docker run ：创建一个新的容器并运行一个命令 <br>  

**语法** <br>
>docker run [OPTIONS] IMAGE [COMMAND] [ARG...] <br>  

**PTIONS说明：** <br>
* -a stdin: 指定标准输入输出内容类型，可选 STDIN/STDOUT/STDERR 三项； <br>
* -d: 后台运行容器，并返回容器ID； <br>
* -i: 以交互模式运行容器，通常与 -t 同时使用； <br>
* -t: 为容器重新分配一个伪输入终端，通常与 -i 同时使用； <br>
* --name="nginx-lb": 为容器指定一个名称； <br>
* --dns 8.8.8.8: 指定容器使用的DNS服务器，默认和宿主一致； <br>
* --dns-search example.com: 指定容器DNS搜索域名，默认和宿主一致； <br>
* -h "mars": 指定容器的hostname； <br>
* -e username="ritchie": 设置环境变量； <br>
* --env-file=[]: 从指定文件读入环境变量； <br>
* --cpuset="0-2" or --cpuset="0,1,2": 绑定容器到指定CPU运行； <br>
* -m :设置容器使用内存最大值； <br>
* --net="bridge": 指定容器的网络连接类型，支持 bridge/host/none/container: 四种类型； <br>
* --link=[]: 添加链接到另一个容器； <br>
* --expose=[]: 开放一个端口或一组端口； <br>  

**实例**<br>
使用docker镜像nginx:latest以后台模式启动一个容器,并将容器命名为mynginx。 <br>
>docker run --name mynginx -d nginx:latest <br>  

使用镜像nginx:latest以后台模式启动一个容器,并将容器的80端口映射到主机随机端口。 <br>
>docker run -P -d nginx:latest <br>  

使用镜像nginx:latest以后台模式启动一个容器,将容器的80端口映射到主机的80端口,主机的目录/data映射到容器的/data。 <br>
>docker run -p 80:80 -v /data:/data -d nginx:latest <br>  

使用镜像nginx:latest以交互模式启动一个容器,在容器内执行/bin/bash命令。 <br>
>panxiang@panxiang:~$ docker run -it nginx:latest /bin/bash <br>
>root@b8573233d675:/#   

## Docker create 命令  

**docker create** ：创建一个新的容器但不启动它  

**语法**
>docker create [OPTIONS] IMAGE [COMMAND] [ARG...]  

语法同 docker run  

**实例**<br>
使用docker镜像nginx:latest创建一个容器,并将容器命名为mynginx <br>
>panxiang@panxiang:~$ docker create  --name mynginx  nginx:latest     
>09b93464c2f75b7b69f83d56a9cfc23ceb50a48a9db7652ee4c27e3e2cb1961f  

## Docker exec 命令  

**docker exec** ：在运行的容器中执行命令  

**语法**
>docker exec [OPTIONS] CONTAINER COMMAND [ARG...]  

OPTIONS说明：
* -d :分离模式: 在后台运行
* -i :即使没有附加也保持STDIN 打开
* -t :分配一个伪终端  

**实例** <br>
在容器mynginx中以交互模式执行容器内/root/baidu.sh脚本 <br>
>panxiang@panxiang:~$ docker exec -it mynginx /bin/sh /root/baidu.sh  
>http://www.baidu.com/  

在容器mynginx中开启一个交互模式的终端<br>
>panxiang@panxiang:~$ docker exec -i -t  mynginx /bin/bash  
>root@b1a0703e41e7:/#


## Docker start/stop/restart 命令  

**docker start** :启动一个或多少已经被停止的容器  

**docker stop** :停止一个运行中的容器  

**docker restart** :重启容器  

**语法**
>docker start [OPTIONS] CONTAINER [CONTAINER...] <br>
>docker stop [OPTIONS] CONTAINER [CONTAINER...] <br>
>docker restart [OPTIONS] CONTAINER [CONTAINER...] <br> 

**实例** <br>
启动已被停止的容器mynginx <br>
>docker start mynginx  

停止运行中的容器mynginx <br>
>docker stop mynginx  

重启容器mynginx <br>
>docker restart mynginx  

## Docker kill 命令  

**docker kill** :杀掉一个运行中的容器。  

**语法**
>docker kill [OPTIONS] CONTAINER [CONTAINER...]  

**OPTIONS说明：**
* -s :向容器发送一个信号  

**实例**<br>
杀掉运行中的容器mynginx <br>
>panxiang@panxiang:~$ docker kill -s KILL mynginx  
>mynginx  

## Docker rm 命令  

**docker rm** ：删除一个或多少容器  

**语法**
>docker rm [OPTIONS] CONTAINER [CONTAINER...]  

**OPTIONS说明：**
* -f :通过SIGKILL信号强制删除一个运行中的容器
* -l :移除容器间的网络连接，而非容器本身
* -v :-v 删除与容器关联的卷  

**实例** <br>
强制删除容器db01、db02 <br>
>docker rm -f db01、db02  

移除容器nginx01对容器db01的连接，连接名db <br>
>docker rm -l db  

删除容器nginx01,并删除容器挂载的数据卷 <br>
>docker rm -v nginx01

