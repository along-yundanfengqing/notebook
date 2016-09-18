#Linux命令


##网络相关


##用户信息传递
*	查看目前系统登录用户

		w
		who

*	查看每个账号最近登录时间

		lastlog	#读取/var/log/lastlog文件

*	和系统上用户聊天

		write 账号 [终端]

*	屏蔽消息

		mesg n	#查看状态使用mesg命令

*	对系统所有用户广播

		wall

*	踢掉登录用户

		pkill -kill -t tty	#桌面用户登录终端为tty7

##终端知识
*	tty
*	pts
*	

##system命令
*	Install linux-header package under Debian or Ubuntu Linux

		apt-get install linux-headers-$(uname -r)

##man
*	man的章节分布
	1.	**Standard commands标准命令**
	2.	System calls系统调用
	3.	Libraryfunctions库函数
	4.	Specialdevices设备说明
	5.	File formats文件格式
	6.	Games and toys游戏和娱乐
	7.	Miscellaneous杂项
	8.	**AdministrativeCommands管理员命令**
	9.	Kernel routines（内核例程，非标准）
	>`man passwd`显示命令passwd
	>
	>`man 5 passwd`显示passwd文件中各个字段含义
*	man查找顺序
	*	`man -M path command`使用`-M path`定义查找目录。
	*	环境变量`MANPATH`
	*	配置文件`/etc/manpath.config`
*	Usage
	*	`man [section] [page]`
	*	-f 查看命令所在章节


##Virtualbox
*	挂载共享磁盘
		
		mount -t vboxsf gongxiang /mnt/shared/

*	自动挂载
		
		/etc/fstab中添加
		gongxiang /mnt/shared vboxsf rw,gid=100,uid=1000,auto 0 0