#Linux编程
##汇编相关
*	as		汇编命令，将汇编程序中的助记符翻译成机器指令
*	ld		链接器，将目标文件链接成可执行文件
	*	修改目标文件中信息，对地址做重定位。
	*	把多个目标文件合并成一个可执行文件
*	xxd		查看二进制文件
*	readelf		分析elf文件（ELF Header & Section Header Table)
	*	-a 显示所有信息
*	hexdump		打印十六进制
	*	-C	canonical hex and ascii display。左边一列文件地址，中间是每个字节的十六进制表示，右边是把字节解释成ascii码对应的字符。中间的*号表示省略的全是0。
	*	-c	one-byte character display。把字节全部打印出来	
*	objdump		查看目标文件或者可执行的目标文件（把程序中的及其指令反汇编disassemble）
	*	-s	--full-contents。显示指定section的完整内容。默认所有非空的section都会被显示。
	*	-S	--source。尽可能反汇编出源代码。
	*	-d	--disassemble。反汇编。左边是机器指令字节，右边是反汇编结果。
	>gcc编译时加上`-g`选项，使用`objdump -dS`反汇编时可以把C代码和汇编代码穿插起来显示。
*	nm		names缩写，列出目标文件中的符号清单（函数和全局变量）
*	ldd		分析程序运行时需要依赖的动态库





##gdb命令
*	start
*	step单步执行命令
*	disassemble反汇编当前函数
*	si一条**指令**一条指令单步调试
*	bt查看每层栈帧上的参数
*	frame查看每层栈帧上的局部变量
*	info registers显示所有寄存器的当前值
*	p $esp打印esp寄存器的值(表示寄存器名称时，前面加上$，esp寄存器指向保存函数栈帧的栈空间栈顶)



##gcc
*	-s	生成汇编代码
*	-c	生成目标文件
*	-E	只做预处理不编译
*	-o	生成文件重命名
*	-lc	链接libc库（默认选项，可不写）
*	-dynamic-linker	指定动态链接器
*	-v	编译详细信息
*	-g	产生调试信息。
	>Produce debugging information in the operating system's native format(stabs).GDB can work with this debugging information.
	>
	>使用`objdump`反汇编时可以把C代码和汇编代码穿插起来显示。





##杂七杂八
*	获取Linux 内存页（基页）大小的命令：`getconf PAGE_SIZE` ，一般的输出是4096，即 4KB。
*	在执行 int 80 指令时，寄存器 eax 中存放的是系统调用的功能号，而传给系统调用的参数则必须按顺序放到寄存器 ebx，ecx，edx，esi，edi 中，当系统调用完成之后，返回值可以在寄存器 eax 中获得。
*	所有的系统调用功能号都可以在文件 /usr/include/bits/syscall.h 中找到，为了便于使用，它们是用 SYS_<name> 这样的宏来定义的，如 SYS_write、SYS_exit 等。
*	ELF文件（Executable and Linking Format,作为应用程序二进制接口）
	*	可重定位的目标文件relocatable （REL可重定位文件）
	*	可执行文件executable （EXEC可执行文件）
	*	共享库sharaed object
*	.bss .data .text区别
	
	*	BSS段
		
		在采用段式内存管理的架构中，BSS段（bss segment）通常是指用来存放程序中未初始化的全局变量的一块内存区域。BSS是英文Block Started by Symbol的简称。BSS段属于静态内存分配。
		
	*	数据段
		
		在采用段式内存管理的架构中，数据段（data segment）通常是指用来存放程序中已初始化的全局变量的一块内存区域。数据段属于静态内存分配。
		
	*	代码段
		
		在采用段式内存管理的架构中，代码段（text segment）通常是指用来存放程序执行代码的一块内存区域。这部分区域的大小在程序运行前就已经确定，并且内存区域属于只读。在代码段中，也有可能包含一些只读的常数变量，例如字符串常量等。

*	使用`gcc -S main.c`，只生成汇编代码main.s，不生成二进制的目标文件。
*	64位cpu汇编寄存器以r开头，32位以e开头。
*	gcc做链接，实际是调用ld来链接。链接crt1.o,64位机器位置为`/usr/lib/x86_64-linux-gnu/crt1.o`,32位机器位置为`/usr/lib/crt1.o`.crti.o



##栈
*	位于内存最顶端。栈从内存顶部向下增长。通过`pushl`将值压入栈顶，其实栈顶是栈内存的**底部**。
*	`%esp`保存**栈顶**指针。
	*	`pushl`数据入栈，`%esp`值减去4，指向新的栈顶。
	*	`popl`数据出栈，	`%esp`值增加4，栈顶值放入指定寄存器。
	*	操作数均为寄存器。
	*	访问栈顶元素，使用间接寻址`%esp`。
	
			movl (%esp),%eax	#访问栈顶值。
			movl 4(%esp),%eax	#访问栈顶下一个值。

*	函数执行
	*	函数所有参数**逆序**入栈。参数**从右至左**压栈。
	*	call指令
		*	下一条指令地址（返回地址）压栈。
		*	修改指令指针`%eip`指向函数起始处。
	*	函数本身所做工作
		*	`pushl %ebp`保存当前基址指针寄存器内容。
		>基址指针，用于访问函数的参数和局部变量。
		*	`movl %esp,%ebp`使参数作为相对于基址指针的固定索引进行访问。**使用栈指针不合适**
		>函数开始时将栈指针复制到基址指针寄存器可以很方便调用参数位置，`%ebp`一直是栈指针在函数开始时的位置，相当于对**栈帧**的常量引用。
		>
		>栈帧：包含函数中使用的所有栈变量，包括参数、局部变量、返回地址。
		
		*	为局部变量保留栈空间，将栈指针下移。
		
				subl $8，%esp	#预留两个字内存，地址分别为-4(%ebp),-8(%ebp)。

*	函数执行完毕
	*	返回值存储到`%eax`。
	*	栈恢复到调用函数时状态（移除当前栈帧，使调用代码栈帧生效）。
	*	控制权交还调用程序。（ret指令实现，弹出栈顶值到指令指针寄存器%eip）。
	*	返回前**必须恢复**前一个栈帧。
		
			movl %ebp,%esp
			popl %ebp
			ret
	*	废弃所有局部变量，控制权转回调用代码，可检查`%eax`中返回值。





##Linux系统编程
###常用头文件
*	stdio.h	标准c输入输出
*	unistd.h	
*	sys/types.h
*	sys/stat.h
*	fcntl.h
*	sys/ioctl.h
*

###Command
*	`strace`	system call tracer监视变量访问
*		