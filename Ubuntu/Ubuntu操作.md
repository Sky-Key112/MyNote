# Ubuntu

## Ubuntu软件升级

        sudo apt-get update
 
        sudo apt-get upgrade
        
        sudo apt-get dist-upgrade
        
        sudo reboot

## 重启&关机命令

        重启:
        sudo reboot
        关机
        sudo shutdown now

## 文件管理
命令: df  du 
查看占用大小
### df
        查看文件系统的信息
        df [选项] [文件名]

        例如:
        df -h

        Filesystem      Size  Used Avail Use% Mounted on
        none            3.8G  4.0K  3.8G   1% /mnt/wsl
        none            466G  271G  195G  59% /usr/lib/wsl/drivers

会显示磁盘存储信息,一般使用参数-h,以G M K 来显示空间,而不是bit.  

**文件名选项是会输出该目录或文件所属的磁盘或分区的大小,而不是文件大小**

参数列表:

        -a, --all 包含全部的文件系统; –block-size=<区块大小>：以指定的区块大小来显示区块数目;
        -h, --human-readable 以可读性较高的方式来显示信息;
        -H, --si 很像 -h, 但在计算时是以1000 Bytes为换算单位而非1024 Bytes;
        -i, --inodes 列出 inode 资讯，不列出已使用 block;
        -k, --kilobytes 就像是指定区块大小(字节) --block-size=1024;
        -l, --local 显示本地端的文件系统;
        -m, --megabytes 就像是指定区块大小(字节) --block-size=1048576; –no-sync：在取得磁盘使用信息前，不要执行sync指令，此为预设值;
        -P, --portability 使用 POSIX 输出格式;
        -t, --type=TYPE 显示指定文件系统类型的磁盘信息;
        -T, --print-type 显示文件系统的形式
        -x, --exclude-type=TYPE 不要显示指定文件系统类型的磁盘信息; – help：显示帮助； – version：显示版本信息。
### du
显示一个目录树及其每个子树的磁盘使用情况(`可指定单一文件`)

        du [-abcDhHklmsSx] [-L<符号连接>] [-X<文件>] [–block-size][–exclude=<目录或文件>] [–max-depth=<目录层数>] [–help] [–version] [目录或文件]

        例如:
        du -h 

        4.0K    ./src/test1/src
        4.0K    ./src/test1/include/test1
        8.0k    .                         # 当前目录总大小

        du -sh
        8.0k    .

        du -sh src/
        5.8M    src/                    #一般会用这个


参数列表:

        -a或-all 为每个指定文件显示磁盘使用情况，或者为目录中每个文件显示各自磁盘使用情况。
        -b或-bytes 显示目录或文件大小时，以byte为单位。
        -c或–total 除了显示目录或文件的大小外，同时也显示所有目录或文件的总和。
        -D或–dereference-args 显示指定符号连接的源文件大小。
        -h或–human-readable 以K，M，G为单位，提高信息的可读性。
        -H或–si 与-h参数相同，但是K，M，G是以1000为换算单位,而不是以1024为换算单位。
        -k或–kilobytes 以1024 bytes为单位。
        -l或–count-links 重复计算硬件连接的文件。
        -L<符号连接>或–dereference<符号连接> 显示选项中所指定符号连接的源文件大小。
        -m或–megabytes 以1MB为单位。
        -s或–summarize 仅显示总计，即当前目录的大小。
        -S或–separate-dirs 显示每个目录的大小时，并不含其子目录的大小。
        -x或–one-file-xystem 以一开始处理时的文件系统为准，若遇上其它不同的文件系统目录则略过。
        -X<文件>或–exclude-from=<文件> 在<文件>指定目录或文件。
        –exclude=<目录或文件> 略过指定的目录或文件。
        –max-depth=<目录层数> 超过指定层数的目录后，予以忽略。
        –help 显示帮助。
        –version 显示版本信息。
        -sh *显示当前目录内文件夹及文件的大小。