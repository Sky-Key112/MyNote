# CMake
[CMake官网](https://cmake.org/documentation/)
[知乎上非常全面的教程](https://www.zhihu.com/column/c_1490802622991306752)
- `CMake`是一个比make更高级的编译配置工具，它可以根据不同平台、不同的编译器，生成相应的Makefile或者vcproj项目。
- 通过编写`CMakeLists.txt`，可以控制生成的`Makefile`，从而控制编译过程。CMake自动生成的Makefile不仅可以通过make命令构建项目生成目标文件，还支持安装（`make install`）、测试安装的程序是否能正确执行（`make test`，或者`ctest`）、生成当前平台的安装包（`make package`）、生成源码包（`make package_source`）、产生Dashboard显示数据并上传等高级功能，只要在`CMakeLists.txt`中简单配置，就可以完成很多复杂的功能，包括写测试用例。
- 如果有嵌套目录，`子目录`下可以有自己的CMakeLists.txt。

## 安装
[下载地址](http://www.cmake.org/cmake/resources/software.html)
1. 根据自己的需要下载相应的包即可，Windows下可以下载zip压缩的绿色版本，还可以下载源代码。
2. 

## 教程
### 最小的cmake配置
```cmake
cmake_minimum_required(VERSION 3.13) # 3.13 or later
project(sample CXX)
add_library(sample sample.cpp)
add_executable(sample_exe sample_exe.cpp)
```
#### 1. cmake_minimum_required

该函数规定了此工程使用的cmake最低版本。

由于cmake仍在不断发展，每个版本均会修改一些函数参数，也会添加更多函数。此函数的作用是为了防止使用版本过低的cmake来配置导致非预期错误

#### 2. project
该函数声明了此项目的名称。

由于一个项目中可能包含多个库或多个可执行程序，在子库/子可执行程序中禁止使用与该函数声明中的相同的名称。该函数第二个参数为该项目的代码类型。可声明 C 或 CXX 或 C CXX。对应的代表了纯c工程，纯c++工程与混合工程。
`注意：声明的代码类型影响了编译器的选取`。
#### 3. add_library / add_executable
该函数声明了添加一个库或添加一个可执行程序。

第一个参数代表了该库/可执行程序的名称。在没有明确声明生成二进制文件名时，也代表了对应生成的二进制文件名。

第二个参数代表了要生成的二进制使用的源文件。这里可以使用列表变量，也可以直接添加源文件名称。当然，也可以在后续使用函数 `target_source` 添加源文件。
   
当然，还可以添加其他关键字例如：
   - `SHARED` 声明该库仅被作为动态库生成
   - `STATIC` 声明该库仅被作为静态库生成
   - `OBJECT` 声明该target仅生成中间binary文件，以供其他target使用
   - `INTERFACE` 声明该库仅是一个接口而并没有属于自己的binary
   - `ALIAS` 声明该库仅是其他库的别名
   - `IMPORTED` 声明该库不需要构建，而是已被导入具体配置。此方式一般存在于依赖提供的配置中。
  
上述关键字只能在 `add_library` 中被声明。

在未声明前五个关键字时，库的构建类型根据 `BUILD_SHARED_LIBS` 变化。

>注意：声明win32可执行程序时，应在`add_executable`中程序名称后添加关键字`WIN32`。

### 关键字
#### 1. project
每个cmake项目均应当声明此关键字，这影响了整个项目的属性。cmake也会提供项目对应的各个变量，例如：
- `PROJECT_NAME` 项目名称
- `PROJECT_SOURCE_DIR` 项目源码根目录
- `PROJECT_VERSION` 项目版本
- `PROJECT_BINARY_DIR` 项目生成的临时二进制目录，用于存放配置/编译中间文件。

#### 2. target
`target`(目标)在cmake中是一个很重要的概念，应当将它理解为一个object(对象)。
- Target 是 CMake 中的一个核心概念，它表示一个构建目标，可以是一个可执行文件、一个库文件或者一个自定义的命令。
- 使用`add_executable()`、`add_library()`、`target_link_libraries()` 命令即刻生成一个target的对象。后续所有操作都是基于对这个对象进行链接、构建。
- `add_custom_target()`：用于定义一个自定义的 Target，可以执行一些特定的命令。
- `Target` 之间可以通过 `target_link_libraries()` 命令来指定链接关系，也可以通过 `target_dependencies()` 命令来指定依赖关系。CMake 还提供了许多以 `target_` 开头的命令来设置 Target 的属性，如 `target_sources()`、`target_include_directories()` 等。
- 常见的target命令:
  - `target_compile_definitions()`: 用于为目标添加编译时的宏定义，相当于 gcc 的 -D 选项。
  - `target_compile_features()`: 用于为目标指定所需的编译器特性，如 cxx_std_11 表示需要支持 C++11 标准。
  - `target_compile_options()`: 用于为目标添加编译选项，如 -Wall -O2 等。
  - `target_include_directories()`: 用于为目标添加头文件搜索路径，相当于 gcc 的 -I 选项。
  - `target_link_directories()`: 用于为目标添加库文件搜索路径，相当于 gcc 的 -L 选项。
  - `target_link_libraries()`: 用于为目标添加链接的库文件，相当于 gcc 的 -l 选项。
  - `target_link_options()`: 用于为目标添加链接选项，如 -pthread -static 等。
  - `target_precompile_headers()`: 用于为目标启用预编译头文件，可以提高编译速度。
  - `target_sources()`: 用于为目标添加源文件，可以在多个地方分别指定源文件。
  
  

#### 3. PUBLC PRIVATE INTERFACE

- `PUBLIC` 声明该关键字后续的值在构建该target时使用，并向下游提供。
- `PRIVATE` 声明该关键字后续的值仅在构建该target时使用，不向下游提供。
- `INTERFACE` 声明该关键字仅向下游提供，不在构建该target时使用。

### 查找依赖

#### 1. find_package
`find_package` 命令是用于查找和加载外部依赖包的配置文件的。

它有两种模式：Module 模式和 Config 模式。
 - Module 模式：在这种模式下，CMake 会搜索一个名为 Find<PackageName>.cmake 的文件，这个文件一般由 CMake 自带或者由用户提供，它负责寻找依赖包的路径、版本、库文件等信息，并设置相应的变量供后续使用。
 - Config 模式：在这种模式下，CMake 会搜索一个名为 <PackageName>Config.cmake 或者 <lowercasePackageName>-config.cmake 的文件，这个文件一般由依赖包自身提供，它直接包含了依赖包的路径、版本、库文件等信息，并提供一些目标或函数供后续使用。

``` cmake
find_package(
<PackageName>    # 是要查找的依赖包的名称，必须指定。
[version]        # 是要求的依赖包的版本号，可选指定。
[EXACT]          # 表示要求找到的依赖包版本必须和指定的版本完全一致，否则会报错。
[QUIET]          # 表示不输出任何信息，只设置变量或目标。
[MODULE]         # 表示强制使用 Module 模式查找依赖包，即使存在 Config 模式的文件。
[REQUIRED]       # 表示如果找不到依赖包，则报错并终止构建过程。
[[COMPONENTS] [components…]]  # 表示指定要查找的依赖包的组件或模块，后面跟随一个或多个组件名称。不同的依赖包可能有不同的组件划分，需要查看相应的文档。
[OPTIONAL_COMPONENTS components…])  # 表示指定要查找的依赖包的可选组件或模块，后面跟随一个或多个组件名称。如果找不到可选组件，则不会报错，但会设置相应的变量。
```
```cmake 
find_package(<PackageName> [version] [EXACT] [QUIET] [MODULE]
             [REQUIRED] [[COMPONENTS] [components...]]
             [OPTIONAL_COMPONENTS components...]
             [REGISTRY_VIEW  (64|32|64_32|32_64|HOST|TARGET|BOTH)]
             [GLOBAL]
             [NO_POLICY_SCOPE]
             [BYPASS_PROVIDER])
```

