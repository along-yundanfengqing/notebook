#Kvm(Kernel-based Virtual Machine)
##Installation
1.	install the qemu-kvm package

		apt-get install qemu-kvm libvirt-bin

2.	put user into the kvm and libvirt groups
	
		adduser <username> kvm
		adduser <username> libvirt

3.	list your domains

		virsh list --all

	or from  non-root user
		
		virsh --connect qemu:///system list --all

4.	If you intend to create VMs from the command-line, install 
		
		virtinst


##Creating a new guest
1.	using GUI application Virtual Machine Manager

		virt-manager

	or create VM guest via command line.
	
		virt-install 


##Setting up bridge networking


##常用命令
*	`virsh`	management user interface
*	`virsh start VMGUEST`	start guest
*	`virsh shutdown VMGUEST`	shutdown guest
*	`virsh destroy VMGUEST`	force shutdown guest





##todo
*	基于 libvirt 的工具如何简化 KVM 虚拟化站点的常见管理任务。这些内容重点介绍了使用 virsh 和 virt-install 命令的命令行示例，但所有这些任务都可在图形化的、基于 libvirt 的 VMM (virt-manager) 中执行。必须以 root 用户身份（或通过 sudo 命令）执行所有这些命令。