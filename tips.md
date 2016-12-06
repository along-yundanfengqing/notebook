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

###	windows系统变量

	%appData%	#对Application Data路径的简记形式。相当于 C:\Documents and Settings\用户目录\Application Data。
	%path%	#列出了可执行文件的搜索路径。


