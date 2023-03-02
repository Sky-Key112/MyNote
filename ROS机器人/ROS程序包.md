# ROS程序包 
可选catkin或者roscreate创建
***
# **1.创建一个catkin程序包**
    catkin_create_pkg <package_name> [depend1] [depend2] [depend3]

    例如:
    catkin_create_pkg package1 std_msgs rospy roscpp

    创建package1程序包,添加了std_msgs rospy roscpp 三个依赖包

## 程序包依赖关系

- 查看一级依赖
  
      rospack depends1 package1

      效果:
      std_msgs
      rospy
      roscpp 
- 全部依赖

      rospack depends package1

      效果:
      cpp_common
      rostime
      roscpp_traits
      roscpp_serialization
      genmsg
      genpy
      message_runtime
      rosconsole
      std_msgs
      rosgraph_msgs
      xmlrpcpp
      roscpp
      rosgraph
      catkin
      rospack
      roslib
      rospy

## 目录结构
>自动生成以下目录

    package_1/
      CMakeLists.txt     -- CMakeLists.txt file for package_1
      package.xml        -- Package manifest for package_1

## 程序包自定义

1. 自定义package.xml
    - 描述标签

          <description>The beginner_tutorials package</description>

      将描述信息修改为任何你喜欢的内容，但是按照约定第一句话应该简短一些，因为它覆盖了程序包的范围。

     - 维护者标签

            <maintainer email="you@yourdomain.tld">Your Name</maintainer>

        1. 这是package.xml中要求填写的一个重要标签，因为它能够让其他人联系到程序包的相关人员。
        2. 至少需要填写一个维护者名称，但如果有需要的话你可以添加多个。
        3. 除了在标签里面填写维护者的名称外，还应该在标签的email属性中填写邮箱地址：
   
     - 许可标签

            <license>BSD</license>

        BSD, MIT, Boost Software License, GPLv2, GPLv3, LGPLv2.1, LGPLv3

     - 依赖项标签
        catkin_create_pkg会自动生成对应的依赖项标签,但如果要在编译和运行中要用到对应的依赖,就必须手动添加到`run_depend标签`中:
    
            <!-- catkin_create_pkg 会自动添加 -->
            <buildtool_depend>catkin</buildtool_depend>

            <build_depend>roscpp</build_depend>
            <build_depend>rospy</build_depend>
            <build_depend>std_msgs</build_depend>

            <!-- 下面为手动添加 -->
            <run_depend>roscpp</run_depend>
            <run_depend>rospy</run_depend>
            <run_depend>std_msgs</run_depend>
2. 自定义 CMakeLists.txt
   ***
# **2.创建一个rosbuild程序包**

在当前目录下创建新包,并指定包依赖.

    roscreate-pkg [package_name] [depend1] [depend2] [depend3]

    例如:
    $ roscd
    $ cd sandbox
    
    roscreate-pkg beginner_tutorials std_msgs rospy roscpp

    效果:
    Creating package directory ~/fuerte_workspace/sandbox/beginner_tutorials
    Creating include directory ~/fuerte_workspace/sandbox/beginner_tutorials/include/beginner_tutorials
    Creating cpp source directory ~/ros/ros_tutorials/beginner_tutorials/src
    Creating python source directory ~/fuerte_workspace/sandbox/beginner_tutorials/src/beginner_tutorials
    Creating package file ~/fuerte_workspace/sandbox/beginner_tutorials/Makefile
    Creating package file ~/fuerte_workspace/sandbox/beginner_tutorials/manifest.xml
    Creating package file ~/fuerte_workspace/sandbox/beginner_tutorials/CMakeLists.txt
    Creating package file ~/fuerte_workspace/sandbox/beginner_tutorials/mainpage.dox