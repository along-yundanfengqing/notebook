#Linux系统编程
##文件系统
###常用命令
*	od		二进制查看工具查看文件系统的所有字节

		od -tx1 -Ax fs

*	debugfs	可以对文件系统进行操作(ext2/ext3/ext4 file system debugger)

		debugfs fs

##进程
*   内核跟踪进程的下列信息
    *   运行位置
    *   访问文件
    *   信用状况（安全机制）
    *   当前目录
    *   访问的内存空间


*   进程的属性
    *    pid
    *   信用状况
    *   setuid、getgid、系统守护进程
    *   uid、gid
    *   