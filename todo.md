*	In Linux, every process has several IDs associated with it, including:

Process ID (PID)

This is an arbitrary number identifying the process. Every process has a unique ID, but after the process exits and the parent process has retrieved the exit status, the process ID is freed to be reused by a new process.
Parent Process ID (PPID)

This is just the PID of the process that started the process in question.
Process Group ID (PGID)

This is just the PID of the process group leader. If PID == PGID, then this process is a process group leader.
Session ID (SID)

This is just the PID of the session leader. If PID == SID, then this process is a session leader.
Sessions and process groups are just ways to treat a number of related processes as a unit. All the members of a process group always belong to the same session, but a session may have multiple process groups.

Normally, a shell will be a session leader, and every pipeline executed by that shell will be a process group. This is to make it easy to kill the children of a shell when it exits. (See exit(3) for the gory details.)

I don't think there is a special term for a member of a session or process group that isn't the leader.


*	ulk
		
	深入理解LINUX内核，很好的LINUX书籍-In-depth understanding of LINUX kernel,

*	APUE
	

	Advanced Programming in the UNIX® Environment

*	ioctl	control device
*	I2C

		I2C（Inter－Integrated Circuit）总线是用于连接微控制器及其外围设备。

*	/sys/class

	该目录下包含所有注册在kernel里面的设备类型，这是按照设备功能分类的设备模型，每个设备类型表达具有一种功能的设备。每个设备类型子目录下都是这种哦哦那个设备类型的各种具体设备的符号链接，这些链接指向/sys/devices/name下的具体设备。设备类型和设备并没有一一对应的关系，一个物理设备可能具备多种设备类型；一个设备类型只表达具有一种功能的设备，比如：系统所有输入设备都会出现在/sys/class/input之下，而不论它们是以何种总线连接到系统的。(/sys/class也是构成linux统一设备模型的一部分)

*	WPA-PSK and WPA2-PSK
{i} Also known as "WPA Personal" and "WPA2 Personal" respectively.

Restrict the permissions of /etc/network/interfaces, to prevent pre-shared key (PSK) disclosure (alternatively use a separate config file such as /etc/network/interfaces.d/wlan0 on newer Debian versions):
# chmod 0600 /etc/network/interfaces
Use the WPA passphrase to calculate the correct WPA PSK hash for your SSID by altering the following example:
$ wpa_passphrase myssid my_very_secret_passphrase
If you don't put the passphrase on the command line, it will be prompted for. The above command gives the output:
network={
        ssid="myssid"
        #psk="my_very_secret_passphrase"
        psk=ccb290fd4fe6b22935cbae31449e050edd02ad44627b16ce0151668f5f53c01b
}
you'll need to copy from "psk=" to the end of the line, to put in your /etc/network/interfaces file.
Open /etc/network/interfaces in a text editor :
# sensible-editor /etc/network/interfaces
Define appropriate stanzas for your wireless interface, along with the SSID and PSK HASH. For example :
auto wlan0
iface wlan0 inet dhcp
        wpa-ssid myssid
        wpa-psk ccb290fd4fe6b22935cbae31449e050edd02ad44627b16ce0151668f5f53c01b
The "auto" stanza will bring your interface up at system startup. If not desired, remove or comment this line.
Save the file and exit the editor.
Bring your interface up. This will start wpa_supplicant as a background process.
# ifup wlan0
Additional wpa-* options are described within /usr/share/doc/wpasupplicant/README.modes.gz. This should also be read if connecting to a network not broadcasting its SSID.

For general /etc/network/interfaces information, see the interfaces(5) man page.

一、查看和修改Linux的时区
1. 查看当前时区
命令 ： "date -R"
2. 修改设置Linux服务器时区
方法 A
命令 ： "tzselect"
方法 B 仅限于RedHat Linux 和 CentOS
命令 ： "timeconfig"
方法 C 适用于Debian
命令 ： "dpkg-reconfigure tzdata"
3. 复制相应的时区文件，替换系统时区文件；或者创建链接文件
cp /usr/share/zoneinfo/$主时区/$次时区 /etc/localtime
例如：在设置中国时区使用亚洲/上海（+8）
cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
二、查看和修改Linux的时间
1. 查看时间和日期
命令 ： "date"
2.设置时间和日期
例如：将系统日期设定成2009年11月3日的命令
命令 ： "date -s 11/03/2009"
将系统时间设定成下午5点55分55秒的命令
命令 ： "date -s 17:55:55"
3. 将当前时间和日期写入BIOS，避免重启后失效
命令 ： "hwclock -w"
 
注：
date
不加参数可以直接看到当前日期时间

cal
不加参数可以直接看到本月月历