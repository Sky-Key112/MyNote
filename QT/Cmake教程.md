# CMake

[CMake官网](https://cmake.org/documentation/)

## 教程

1. 任何项目的最顶部`CMakeLists.txt`必须以指定最小CMake开始 版本使用`cmake_minimum_required()` 命令。这就确立了 策略设置，并确保以下CMake函数使用 CMake的兼容版本。
2. 


    ```cmake
    cmake_minimum_required(VERSION 3.13) # 3.13 or later
    ```