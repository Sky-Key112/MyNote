# ROS话题

节点与节点之间通过一个`ROS话题`来相互通信的
ROS话题`rostopic`,可以看成是一个文件,拥有发布者和订阅者.

![topic_gif](./img/Topic-MultiplePublisherandMultipleSubscriber.gif)

下面我们使用小乌龟来举例
1. 首先确保roscore正在运行, 打开一个新终端：

        $ roscore
2. 打开新终端,运行turtlesim

        $ rosrun turtlesim turtlesim_node
3. 通过键盘遥控turtle

        $ rosrun turtlesim turtle_teleop_key

这样我们就集齐了话题的发布者与订阅者了,下面进行可视化安装,方便理解.
## 使用rqt_graph
使用rqt_graph,可以可视化的看到话题的状态
rqt_graph用动态的图显示了系统中正在发生的事情。rqt_graph是rqt程序包中的一部分。如果你发现没有安装，请：

    $ sudo apt-get install ros-<distro>-rqt
    $ sudo apt-get install ros-<distro>-rqt-common-plugins

    将<distro>替换成你安装的ROS发行版简称（比如kinetic或noetic等）。

然后打开新终端:

    $ rosrun rqt_graph rqt_graph

如图所示:
![rqt_graph](img/rqt_graph_turtle_key2.png)

其中 蓝色和绿色 都是node节点,箭头的指向代表了发布与订阅.中间红色的便是topic话题.

## rostopic命令

    rostopic -h

    rostopic is a command-line tool for printing information about ROS Topics.
    Commands:
            rostopic bw     display bandwidth used by topic
            rostopic delay  display delay of topic from timestamp in header
            rostopic echo   print messages to screen
            rostopic find   find topics by type
            rostopic hz     display publishing rate of topic    
            rostopic info   print information about active topic
            rostopic list   list active topics
            rostopic pub    publish data to topic
            rostopic type   print topic or field type

    Type rostopic <command> -h for more detailed usage, e.g. 'rostopic echo -h'

### rostopic echo
  `rostopic echo`可以显示在某个话题上发布的数据,但同时也会生成一个订阅者,也就是rqt图上的绿色位置.

用法:
    
    rostopic echo [topic]

    $ rostopic echo /turtle1/cmd_vel

    具体topic名称,需要查阅各软件包的文档说明

### 使用rostopic list
`rostopic list`能够列出当前已被订阅和发布的所有话题.

    $ rostopic list -h

    Usage: rostopic list [/topic]

    Options:
    -h, --help            show this help message and exit
    -b BAGFILE, --bag=BAGFILE
                            list topics in .bag file
    -v, --verbose         list full details about each topic
    -p                    list only publishers
    -s                    list only subscribers

一般使用`rostopic list -v`,查看所有列表,并显示全部信息.

    Published topics:
    * /turtle1/color_sensor [turtlesim/Color] 1 publisher
    * /turtle1/cmd_vel [geometry_msgs/Twist] 1 publisher
    * /rosout [rosgraph_msgs/Log] 2 publishers
    * /rosout_agg [rosgraph_msgs/Log] 1 publisher
    * /turtle1/pose [turtlesim/Pose] 1 publisher

    Subscribed topics:
    * /turtle1/cmd_vel [geometry_msgs/Twist] 1 subscriber
    * /rosout [rosgraph_msgs/Log] 1 subscriber
***
## ROS消息

话题的通信是通过节点间发送ROS消息实现的。为了使发布者（turtle_teleop_key）和订阅者（turtulesim_node）进行通信，发布者和订阅者必须发送和接收相同类型的消息。这意味着话题的类型是由发布在它上面消息的类型决定的。使用rostopic type命令可以查看发布在话题上的消息的类型。 

>即,topic话题传递的 就是消息,消息的结构跟`C语言的结构体`很类似.

### 使用rostopic type
rostopic type命令用来查看所发布话题的消息类型。 

用法：

    rostopic type [topic]

    运行：
    $ rostopic type /turtle1/cmd_vel

    你会看到：
    geometry_msgs/Twist

其中`geometry_msgs/Twist`就是话题`/turtle1/cmd_vel`的消息类型 

我们可以使用rosmsg查看消息的详细信息：

    $ rosmsg show geometry_msgs/Twist

    结果:
    geometry_msgs/Vector3 linear
    float64 x
    float64 y
    float64 z
    geometry_msgs/Vector3 angular
    float64 x
    float64 y
    float64 z
后续会了解到 消息的结构是如何生成的.

### rostopic pub(发布话题)
rostopic pub可以把数据发布到当前某个正在广播的话题上。

用法：

    rostopic pub [topic] [msg_type] [args]

在ROS Hydro及更新版本中，示例：

    $ rostopic pub -1 /turtle1/cmd_vel geometry_msgs/Twist -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, 1.8]'

参数分析:

- 这条命令将消息发布到指定的话题：
  
        rostopic pub   

- 这一选项会让rostopic只发布一条消息，然后退出：
  
        -1 

- 这是要发布到的话题的名称：
    
        turtle1/cmd_vel

- 这是发布到话题时要使用的消息的类型：
    
        geometry_msgs/Twist

- 这一选项（两个破折号）用来告诉选项解析器，表明之后的参数都不是选项。如果参数前有破折号（-）比如负数，那么这是必需的。
    
        --

- 如前所述，一个turtlesim/Velocity消息有两个浮点型元素：linear和angular。在本例中，'[2.0, 0.0, 0.0]'表示linear的值为x=2.0, y=0.0, z=0.0，而'[0.0, 0.0, 1.8]'是说angular的值为x=0.0, y=0.0, z=1.8。 

        '[2.0, 0.0, 0.0]' '[0.0, 0.0, 1.8]' 

>这些参数实际上使用的是YAML语法，在YAML命令行文档中有描述。

