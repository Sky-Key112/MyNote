## 打包

1. 在程序中找到QT的编译器-`Qt6.5.0 (MinGW 11.2.0 64-bit)`
2. cd /d 对应目录。 (cd /d表示可跨磁盘)
3. windeployqt 对应.exe文件 （记得加.exe后缀）

## 打包成单文件

1. 下载软件`Enigma Virtual Box`
2. 安装使用，选择主程序
3. 在文件内点添加，讲整个文件夹添加进来，然后剔除无效的文件
4. 文件选项启动压缩
5. 执行封包


## 第三方库编译

### C++ DataFrame

    mkdir [Debug | Release]
    cd [Debug | Release]
    cmake -DCMAKE_BUILD_TYPE=[Debug | Release] -DHMDF_BENCHMARKS=1 -DHMDF_EXAMPLES=1 -DHMDF_TESTING=1 ..
    make
    make install

    cd [Debug | Release]
    make uninstall

    有时候cmake会使用ninja，只需要将make 替换成ninja，同理ninja install也是一样的
`ninja install` 后会在C盘生成一个`libDataFrame.a`文件，在qt的.pro文件中导入即可。 
.a 文件为静态库,编译后无需dll。不能使用vcpkg的包，那个包无法在自有环境下使用。