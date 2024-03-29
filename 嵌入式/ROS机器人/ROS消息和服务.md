# ROS服务（Services）

## rosservice
服务（Services）是节点之间通讯的另一种方式。服务允许节点发送一个请求（request）并获得一个响应（response）。 

用法：

    rosservice list         输出活跃服务的信息
    rosservice call         用给定的参数调用服务
    rosservice type         输出服务的类型
    rosservice find         按服务的类型查找服务
    rosservice uri          输出服务的ROSRPC uri

再让我们看看服务具有参数的情况。查看spawn（产卵）服务的信息：

    $ rosservice type /spawn | rossrv show
    float32 x                               
    float32 y
    float32 theta
    string name
    ---                                    #在分割线之前为参数，之后为响应的类型
    string name
所以，这个服务能让我们可以在给定的位置和角度生成一只新的乌龟。name字段是可选的，这里我们不设具体的名字，让turtlesim自动创建一个。

    $ rosservice call /spawn 2 2 0.2 ""

    参数为上方的 x，y，theta，name（""为空白）；
该调用返回了新产生的乌龟的名字：

    name: turtle2

## rosparam

rosparam能让我们在ROS参数服务器（Parameter Server）上存储和操作数据。参数服务器能够存储整型（integer）、浮点（float）、布尔（boolean）、字典（dictionaries）和列表（list）等数据类型。`rosparam使用YAML标记语言`的语法。一般而言，YAML的表述很自然：1是整型，1.0是浮点型，one是字符串，true是布尔型，[1, 2, 3]是整型组成的列表，{a: b, c: d}是字典。rosparam有很多命令可以用来操作参数，如下所示：

用法：

    rosparam set            设置参数
    rosparam get            获取参数
    rosparam load           从文件中加载参数
    rosparam dump           向文件中转储参数
    rosparam delete         删除参数
    rosparam list           列出参数名

# 创建ROS消息和服务

## msg和srv介绍

msg（消息）：msg文件就是文本文件，用于描述ROS消息的字段。它们用于为不同编程语言编写的消息生成源代码。

srv（服务）：一个srv文件描述一个服务。它由两部分组成：请求（request）和响应（response）。

msg文件存放在软件包的`msg`目录下，srv文件则存放在`srv`目录下。

msg文件就是简单的文本文件，每行都有一个字段类型和字段名称。可以使用的类型为：

    int8, int16, int32, int64 (以及 uint*)
    float32, float64
    string
    time, duration
    其他msg文件
    variable-length array[] 和 fixed-length array[C]

ROS中还有一个特殊的数据类型：`Header`，它含有时间戳和ROS中广泛使用的坐标帧信息。在msg文件的第一行经常可以看到`Header` `header`。

下面是一个使用了Header、字符串原语和其他两个消息的示例： 下面是一个msg文件的样例，它使用了Header，string，和其他另外两个消息的类型：

    Header header
    string child_frame_id
    geometry_msgs/PoseWithCovariance pose
    geometry_msgs/TwistWithCovariance twist

srv文件和msg文件一样，只是它们包含两个部分：请求和响应。这两部分用一条---线隔开。下面是一个srv文件的示例：

    int64 A
    int64 B
    ---
    int64 Sum

    A和B是请求, Sum是响应。

## 使用msg

下面，我们将在之前创建的软件包里定义一个新的消息。

    $ roscd beginner_tutorials
    $ mkdir msg
    $ echo "int64 num" > msg/Num.msg

1

    ##在此声明和构建消息、服务或操作
    ##套餐，按照如下步骤操作：
    ##*让MSG_DEP_SET为您在中使用的消息类型的包集
    ##您的消息/服务/动作(如std_msgs、actionlib_msgs等)。
    ##*在Package.xml文件中：
    ##*MESSAGE_GENERATION添加Build_Depend标签
    ##*为MSG_DEP_SET中的每个包添加BUILD_Depend和EXEC_Depend标签
    ##*如果MSG_DEP_SET不为空，则已拉入以下依赖项
    ##但仍然可以肯定地声明：
    ##*为Message_Runtime添加EXEC_Depend标签
    ##*此文件(CMakeLists.txt)中：
    ##*将MESSAGE_GENERATION和MSG_DEP_SET中的每个包添加到
    ##Find_Package(Catkin必需组件...)
    ##*将Message_Runtime和MSG_DEP_SET中的每个包添加到
    ##Catkin_Package(Catkin_Depends...)
    ##*根据需要取消对下面的添加_*_文件部分的注释
    ##列出每个需要处理的.msg/.srv/.action文件
    ##*取消注释下面的GENERATE_MESSAGE条目
    ##*将MSG_DEP_SET中的每个包添加到GENERATE_MESSAGE(依赖...)
