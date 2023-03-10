# docker操作
## 基本操作

下载镜像:

    docker pull mysql
运行容器:

    docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
    docker run -d mysql --name=mysql 
 
## docker网络

Docker 提供如下 5 种原生的 Network drivers

| 模型 | 说明 | 
|-     |    -| 
|bridge     | 默认 网络驱动程序。主要用于多个容器在同一个Docker宿主机上进行通信（当创建新容器时，默认就是bridge） |
|host       | 容器加入到宿主机的Network namespace，容器直接使用宿主机网络（注意端口不能冲突）网卡数和物理机网卡数量相同|
|none	    |none 网络中的容器，不能与外部通信（只有一块lo网卡）      只有一块网卡|
|Overlay	|Overlay 网络基于 Linux 网桥和 Vxlan，实现跨主机的容器通信|
|Macvlan	|Macvlan 用于跨主机通信场景|

查看网络列表

    docker network ls
一般默认会有3个

    NETWORK ID     NAME      DRIVER    SCOPE
    924cc689ddb3   bridge    bridge    local
    211fb7c03fb9   host      host      local
    294dc78cfb19   none      null      local

所有容器若没有指定网桥,会自动分配到bridge.

docker network 命令表

    docker network 
    Usage:  docker network COMMAND
    Manage networks

    Commands:
    connect     Connect a container to a network
    create      Create a network
    disconnect  Disconnect a container from a network
    inspect     Display detailed information on one or more networks
    ls          List networks
    prune       Remove all unused networks
    rm          Remove one or more networks




## docker容器 mysql

账户
>root   673935394
>gogs   123

### docker 部署 mysql

        docker pull mysql:5.7
        拉取镜像,小服务器选5.7,资源占用少
        没有tag默认拉最新版8.0

运行参数详情

        docker run \
        -d \
        --name mysql \
        -p 33308:3306 \
        -v mysql:/etc/mysql/conf.d \
        -v mysql:/var/lib/mysql \ 
        -e MYSQL_ROOT_PASSWORD=673935394 \ 
        mysql:5.7

        -d 表示让容器在后台运行
        --name 为容器起一个名字
        -p 映射端口，这里把容器内的 3306 端口映射到了宿主机的 3309
        -v 挂载卷，冒号前是宿主机目录，冒号后是容器内目录
        -e 容器的环境配置

一键复制:

        docker run -d --name mysql -p 33308:3306 -v mysql:/etc/mysql/conf.d -v mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=673935394 mysql
