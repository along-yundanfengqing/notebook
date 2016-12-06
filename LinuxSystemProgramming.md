#Linux系统编程
##文件系统
###常用命令
*	od		二进制查看工具查看文件系统的所有字节

		od -tx1 -Ax fs

*	debugfs	可以对文件系统进行操作(ext2/ext3/ext4 file system debugger)

		debugfs fs

