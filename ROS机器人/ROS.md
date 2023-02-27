# **ROS机器人**

## **介绍**

- 下位机采用Arduino控制方向舵机与后驱马达

## **ROS本地Ubuntu镜像**
 
 ### 微雪镜像
   1. 下载微雪官网提供的VMware镜像,
   2. 使用StarWind V2V Converter转换成hype-V镜像
   3. 新建虚拟机
   4. 新建虚拟交换机,使用桥接模式.
   5. 按[**微雪教程**](https://www.waveshare.net/wiki/JetRacer_ROS_AI_Kit)配置多机控制.

### docker部署ROS镜像
    容器在默认环境下,无法连接到宿主局域网.
    可以使用macvlan配置,但物理网卡不一定支持. 
    