# **ROS机器人**

## **介绍**

ROS最高支持到Ubuntu 20.04,最新版Ubuntu 22.04只能使用ROS2.

## **ROS Ubuntu安装指南**

[ROS官方中文教程连接](http://wiki.ros.org/cn/noetic/Installation/Ubuntu)

    1.设置sources.list 更换清华镜像
    sudo sh -c '. /etc/lsb-release && echo "deb http://mirrors.tuna.tsinghua.edu.cn/ros/ubuntu/ `lsb_release -cs` main" > /etc/apt/sources.list.d/ros-latest.list'

    2.设置秘钥
    sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654

    3.更新软件包索引
    sudo apt update
    
    4.下载安装 推荐Desktop-Full
    除了桌面版的全部组件外，还包括2D/3D模拟器（simulator）和2D/3D 感知包（perception package）

    sudo apt install ros-noetic-desktop-full  

    可选: [ros-noetic-desktop]、[ros-noetic-ros-base](仅骨架,没有gui界面)
  
## ROS 运行配置

查看或搜索所有可用的软件包，请参见[ROS Index](https://index.ros.org/packages/page/1/time/#noetic)或使用:

    apt search ros-noetic


### **设置环境**

> 每次启动Ubuntu使用ROS都需要运行source脚本

    source /opt/ros/noetic/setup.bash
>Ubuntu自启动配置,新建shell窗口的时候 自动运行source脚本

    echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
    source ~/.bashrc

  `bashrc就是每次自动运行的脚本,将setup.bash添加到bashrc中,即可实现自启动,可以通过修改setup.bash脚本更换不同的ROS版本.`

### 创建ROS工作空间

    $ mkdir -p ~/catkin_ws/src
    $ cd ~/catkin_ws/
    $ catkin_make

    ~为home目录下,当前用户的文档
    创建文件夹后,使用catkin_make命令构建catkin软件包


***
 ### 微雪镜像
   1. 下载微雪官网提供的VMware镜像,
   2. 使用StarWind V2V Converter转换成hype-V镜像
   3. 新建虚拟机
   4. 新建虚拟交换机,使用桥接模式.
   5. 按[**微雪教程**](https://www.waveshare.net/wiki/JetRacer_ROS_AI_Kit)配置多机控制.
***
### docker部署ROS镜像
  已有社区 [`鱼香ROS`](https://www.fishros.org.cn/forum/)
  可以一键部署docker
    
***