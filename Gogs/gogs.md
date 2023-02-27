# **Gogs**

## **介绍**

个人搭建git，GitHub gogs项目，最低可以在树莓派上运行，比gitlab需要的配置低。
***
## **docker部署**

    # Pull image from Docker Hub.
    $ docker pull gogs/gogs

    # Create local directory for volume.
    $ mkdir -p /var/gogs

    # Use `docker run` for the first time.
    $ docker run --name=gogs -p 10022:22 -p 10880:3000 -v /var/gogs:/data gogs/gogs

    # Use `docker start` if you have stopped it.
    $ docker start gogs
***
## **gogs首次安装**
1. 浏览器输入`localhost:10880`首次进入为配置界面
2. 需要选择数据库，推荐使用MySQL，方便快捷。
3. 监听端口写22跟3000
***
## ***踩坑***

    监听端口使用3000,而不是10880.
    配置的url链接可以填108800,这个是生成git链接的.
    内部监听只有3000端口
