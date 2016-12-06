###	tty终端禁止响铃
	
	#setterm -blength 0

###	wpa_supplicant连接wpa加密无线网络

	wpa_passphrase ESID password>>/etc/wpa_supplicant/wpa_supplicant.conf
	systemctl enable wpa_supplicant
	systemctl start wpa_supplicant

> ###	WPA-PSK and WPA2-PSK
>  Also known as "WPA Personal" and "WPA2 Personal" respectively.
> 
> Restrict the permissions of /etc/network/interfaces, to prevent pre-shared key (PSK) disclosure (alternatively use a separate config file such as /etc/network/interfaces.d/wlan0 on newer Debian versions):
> 
	# chmod 0600 /etc/network/interfaces

> Use the WPA passphrase to calculate the correct WPA PSK hash for your SSID by altering the following example:
> $ wpa_passphrase myssid my_very_secret_passphrase
> If you don't put the passphrase on the command line, it will be prompted for. The above command gives the output:
>	
	network={
	         ssid="myssid"
		     #psk="my_very_secret_passphrase"
	         psk=ccb290fd4fe6b22935cbae31449e050edd02ad44627b16ce0151668f5f53c01b
	 		}

> you'll need to copy from "psk=" to the end of the line, to put in your /etc/network/interfaces file.
> Open /etc/network/interfaces in a text editor :
>
	 # sensible-editor /etc/network/interfaces

> Define appropriate stanzas for your wireless interface, along with the SSID and PSK HASH. For example :
> 
 	auto wlan0
 	iface wlan0 inet dhcp
         wpa-ssid myssid
         wpa-psk ccb290fd4fe6b22935cbae31449e050edd02ad44627b16ce0151668f5f53c01b

> The "auto" stanza will bring your interface up at system startup. If not desired, remove or comment this line.
> Save the file and exit the editor.
> Bring your interface up. This will start wpa_supplicant as a background process.
> 
	 # ifup wlan0
> 
> Additional wpa-* options are described within /usr/share/doc/wpasupplicant/README.modes.gz. This should also be read if connecting to a network not broadcasting its SSID.
> 
> For general /etc/network/interfaces information, see the interfaces(5) man page.

###	debian开机启动服务设置(update-rc.d)
	
	update-rc.d servicesname disable		#禁止开机启动
	update-rc.d	servicesname enable		#可以开机启动
	service --status-all		#查看所有服务运行状态的命令，+正在运行，-没有运行，？不详
	
	sysv-rc-conf也可用来查看服务状态





###	Retext工具栏图标丢失

1.  运行命令

        python3 -c "from gi.repository import Gtk; print(Gtk.Settings.get_default().get_property('gtk-icon-theme-name'))"


1.  设置参数

    *   通过菜单修改。
    
        编辑&rarr;`preferences`中，设置   `Icon theme name`。
    
    *   通过配置文件修改。
       
        编辑  `~/.config/ReText projiect/Retext.conf`，添加一行代码   `iconTheme=Adwaita`（其中`Adwaita`为命令的输出值）


3.	有序列表重新编序号问题

	*   问题：如上例，假如在**运行命令**之后的代码使用` ``` `声明的话，将会导致后一个**设置参数**重新编号。
	*   解决方法：使用缩进8个空格的方法，表明为代码区域。


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