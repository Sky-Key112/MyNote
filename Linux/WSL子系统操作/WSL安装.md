# Windows的Linux子系统
适用于 Linux 的 Windows 子系统可让开发人员按原样运行 GNU/Linux 环境 - 包括大多数命令行工具、实用工具和应用程序 - 且不会产生传统虚拟机或双启动设置开销。

## WSL版本比较 

### WSL2

新版为WSL2,一般都用这个,基于hyper-v 虚拟机.缺点是安装了自带的hyper-v之后`无法使用安卓模拟器`.

### WSL
旧版WSL,基于传统的虚拟机模式,但Linux内核不完整,不如直接安装虚拟机,就剩个轻量化的优点了.

## windows终端
`Windows Terminal`就是win的powershell的终端,直接在[微软商店](https://aka.ms/terminal)安装,win10/11自带,版本太旧不好用,建议都升级一下.

高级使用说明可以去[微软官网](https://learn.microsoft.com/zh-cn/windows/terminal/install)看

## WSL安装

1. 控制面板->程序->启动或关闭windows功能,开启`hyper-v`、`适用于Linux的windows子系统`,
2. 以管理员模式打开powershell,既上边的`Windows Terminal`,运行`wsl --install`,自动安装。也可以加上`--no-distribution`,只安装WSL组件,不安装发行版。(默认自动安装会自动下载store里的WSL发行版)
3. 在store里找到适合自己的发行版安装,比如`Ubuntu`,建议安装带版本后缀的,否则Ubuntu会自动更新为最新版本,比如20.04版本会大跳到22.04版本,可能会引发兼容性问题。
4. `wsl --set-default-version 2` 设置WSL2为默认版本

### WSL基本命令

直接去官网看吧,不复制粘贴了。[跳转链接](https://learn.microsoft.com/zh-cn/windows/wsl/basic-commands#install)

### 启动
安装好发行版之后,会在`Windows Terminal`上选择对应的版本启动,没有的话就需要自己设置。
自己设置去看[微软官网](https://learn.microsoft.com/zh-cn/windows/terminal/install)

## docker

特别说明一下,win版的docker也可以是WSL的,使用`wsl -l -v`可以查看docker的虚拟机,会有2个。一个是data一个直接是desktop。

WSL的版本可以在`docker_desktop`的Setting->Resources->Advanced中设置。建议用WSL2,比1好太多了。
