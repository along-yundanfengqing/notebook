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