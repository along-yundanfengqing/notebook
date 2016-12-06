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


%SystemDrive% 操作系统所在的分区号。如 C: 
%SystemRoot% 操作系统根目录。如 C:\WINDOWS 
%windir% 操作系统根目录。如 C:\WINDOWS 
%ALLUSERSPROFILE% 相当于 C:\Documents and Settings\All Users 
%APPDATA% 相当于 C:\Documents and Settings\用户目录\Application Data 
%ProgramFiles% 相当于 C:\Program Files 
%CommonProgramFiles% 相当于 C:\Program Files\Common Files 
%HOMEDRIVE% 操作系统所在的分区号。如：C: 
%HOMEPATH% 相当于 \Documents and Settings\用户目录 
%USERPROFILE% 相当于 C:\Documents and Settings\用户目录 
%HOMEDRIVE% = C:\ 当前启动的系统的所在分区 
%SystemRoot% = C:\WINDOWS 当前启动的系统的所在目录 
%windir% = %SystemRoot% = C:\WINDOWS 当前启动的系统的所在目录 
%USERPROFILE% = C:\Documents and Settings\minamiko 当前用户数据变量 
%HOMEPATH% = C:\Documents and Settings\minamiko 当前用户环境变量 
%system% = C:\WINDOWS\SYSTEM32 
%ALLUSERSPROFILE% ： 列出所有用户Profile文件位置。 
%APPDATA% : 列出应用程序数据的默认存放位置。 
%CD% : 列出当前目录。 
%CLIENTNAME% : 列出联接到终端服务会话时客户端的NETBIOS名。 
%CMDCMDLINE% : 列出启动当前cmd.exe所使用的命令行。 
%CMDEXTVERSION% : 命令出当前命令处理程序扩展版本号。 
%CommonProgramFiles% : 列出了常用文件的文件夹路径。 
%COMPUTERNAME% : 列出了计算机名。 
%COMSPEC% : 列出了可执行命令外壳（命令处理程序）的路径。 
%DATE% : 列出当前日期。 
%ERRORLEVEL% : 列出了最近使用的命令的错误代码。 
%HOMEDRIVE% : 列出与用户主目录所在的驱动器盘符。 
%HOMEPATH% : 列出用户主目录的完整路径。 
%HOMESHARE% : 列出用户共享主目录的网络路径。 
%LOGONSEVER% : 列出有效的当前登录会话的域名控制器名。 
%NUMBER_OF_PROCESSORS% : 列出了计算机安装的处理器数。 
%OS% : 列出操作系统的名字。(Windows XP 和 Windows 2000 列为 Windows_NT.) 
%PATHEXT% : 列出操作系统认为可被执行的文件扩展名。 
%PROCESSOR_ARCHITECTURE% : 列出了处理器的芯片架构。 
%PROCESSOR_IDENTFIER% : 列出了处理器的描述。 
%PROCESSOR_LEVEL% : 列出了计算机的处理器的型号。 
%PROCESSOR_REVISION% : 列出了处理器的修订号。 
%ProgramFiles% : 列出了Program Files文件夹的路径。 
%PROMPT% : 列出了当前命令解释器的命令提示设置。 
%RANDOM% : 列出界于0 和 32767之间的随机十进制数。 
%SESSIONNAME% : 列出连接到终端服务会话时的连接和会话名。 
%SYSTEMDRIVE% : 列出了Windows启动目录所在驱动器。 
%SYSTEMROOT% : 列出了Windows启动目录的位置。 
%TEMP% and %TMP% : 列出了当前登录的用户可用应用程序的默认临时目录。 
%TIME% : 列出当前时间。 
%USERDOMAIN% : 列出了包含用户帐号的域的名字。 
%USERNAME% : 列出当前登录的用户的名字。 
%USERPROFILE% : 列出当前用户Profile文件位置。 
%WINDIR% : 列出操作系统目录的位置。 
变量 类型 描述 
%ALLUSERSPROFILE% 本地 返回“所有用户”配置文件的位置。 
%APPDATA% 本地 返回默认情况下应用程序存储数据的位置。 
%CD% 本地 返回当前目录字符串。 
%CMDCMDLINE% 本地 返回用来启动当前的 Cmd.exe 的准确命令行。 
%CMDEXTVERSION% 系统 返回当前的“命令处理程序扩展”的版本号。 
%COMPUTERNAME% 系统 返回计算机的名称。 
%COMSPEC% 系统 返回命令行解释器可执行程序的准确路径。 
%DATE% 系统 返回当前日期。使用与 date /t 命令相同的格式。由 Cmd.exe 生成。有关 date 命令的详细信息，请参阅 Date。 
%ERRORLEVEL% 系统 返回上一条命令的错误代码。通常用非零值表示错误。 
%HOMEDRIVE% 系统 返回连接到用户主目录的本地工作站驱动器号。基于主目录值而设置。用户主目录是在“本地用户和组”中指定的。 
%HOMEPATH% 系统 返回用户主目录的完整路径。基于主目录值而设置。用户主目录是在“本地用户和组”中指定的。 
%HOMESHARE% 系统 返回用户的共享主目录的网络路径。基于主目录值而设置。用户主目录是在“本地用户和组”中指定的。 
%LOGONSERVER% 本地 返回验证当前登录会话的域控制器的名称。 
%NUMBER_OF_PROCESSORS% 系统 指定安装在计算机上的处理器的数目。 
%OS% 系统 返回操作系统名称。Windows 2000 显示其操作系统为 Windows_NT。 
%PATH% 系统 指定可执行文件的搜索路径。 
%PATHEXT% 系统 返回操作系统认为可执行的文件扩展名的列表。 
%PROCESSOR_ARCHITECTURE% 系统 返回处理器的芯片体系结构。值：x86 或 IA64（基于 Itanium）。 
%PROCESSOR_IDENTFIER% 系统 返回处理器说明。 
%PROCESSOR_LEVEL% 系统 返回计算机上安装的处理器的型号。 
%PROCESSOR_REVISION% 系统 返回处理器的版本号。 
%PROMPT% 本地 返回当前解释程序的命令提示符设置。由 Cmd.exe 生成。 
%RANDOM% 系统 返回 0 到 32767 之间的任意十进制数字。由 Cmd.exe 生成。 
%SYSTEMDRIVE% 系统 返回包含 Windows server operating system 根目录（即系统根目录）的驱动器。 
%SYSTEMROOT% 系统 返回 Windows server operating system 根目录的位置。 
%TEMP% 和 %TMP% 系统和用户 返回对当前登录用户可用的应用程序所使用的默认临时目录。有些应用程序需要 TEMP，而其他应用程序则需要 TMP。 
%TIME% 系统 返回当前时间。使用与 time /t 命令相同的格式。由 Cmd.exe 生成。有关 time 命令的详细信息，请参阅 Time。 
%USERDOMAIN% 本地 返回包含用户帐户的域的名称。 
%USERNAME% 本地 返回当前登录的用户的名称。 
%USERPROFILE% 本地 返回当前用户的配置文件的位置。 
%WINDIR% 系统 返回操作系统目录的位置。 
%temp% = %USERPROFILE%\Local Settings\Temp = C:\Documents and Settings\minamiko\Local Settings\Temp 当前用户TEMP缓存变量