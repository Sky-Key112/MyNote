# 移动光猫获取超级密码

## 1. 开启Telnet
 ```
192.168.1.1/webcmcc/telnet.html?password=!@qw34er&username=root
```
在web浏览器输入该链接
 ```
192.168.1.1/webcmcc/telnet.html
//某些情况下 这样也行，不需要帐号密码
```

## 2. 通过Telnet进入光猫的系统

1. 在cmd或win终端输入 

```
telnet 192.168.1.1 
```
提示`Telnet`命令不存在则前往`控制面板`-`程序`-`启用或关闭Windows功能`-找到`Telnet客户端` 勾选`√`
2. 然后使用光猫背后的普通账户`user` 直接登录
3. 找备份文件直接看密码
```
cd /config/workb 
`config`文件夹下会有很多work workA/B/C这种文件夹 都可以进去看看 我这里是workb里边有
ls 
找到一个lastgood.xml文件 类似名字的也行 有备份前缀的一样好用
vi lastgood.xml

/AccountName 
搜索AccountName 然后找到CMCCAdmin 账户 下边就是默认的超级密码
```

4. 记下密码 然后正常的在192.168.1.1登录 就可以有全部设置的权限了

## 备注
其实这个难度主要在开启Telnet，我使用这个功能应该是默认就开启Telnet的或者完全没设防。

本次测试可用型号`HG51e` 
