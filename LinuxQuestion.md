##Linux基础试题
1、	如果你使用一个普通账户telnet远程登录到linux系统中，如何改变身份以root权限管理系统？ （） 
    A 、chmod  B、 chown  C、 chusr  D、su
2、	以下哪个环境变量表示当前路径 （）
    A 、PATH  B、 PWD  C、 HOME  D、ROOT
3、	在cenos系统中，小王希望将他执行的ls命令的输出结果保存在当前目录下文件output.ls中，以供日后进行分析和使用，但要求不覆盖原文件的内容，他应该使用的命令是（）
    A 、ls>output.ls  B、ls>>output.ls  C、ls<<output.ls D、ls-output.ls
4、	权限为765的文件，下列哪个是正确的权限位标记?（）
A、	-rw-rw-r-x  B、-rw-r-xr-r  C、-rwxrw-r-x  D、-rwxr-xrwx
5、	以下函数中，和其他函数不属于一类的是____。
    A、strncpy  B、strtok  C、snprintf  D、strncat
6、	Linux进程中，应用的运行起始地址是一样的，是如何做到的？（）
    A、	编译时区分 B、使用虚拟地址映射 C、运行时分配不一样的地址 D、指定物理地址
7、	下列关于网络编程的描述中,错误的是? （）
    A、	一个 Socket 可以绑定多个网卡
    B、	TCP和UDP协议不能绑定同一个端口
    C、	客户端和服务器端都可以主动关闭 Socket
    D、	Socket支持阻塞和非阻塞模式
8、	以下关于linux操作系统中硬链接和软链接的描述,正确的是?
    A、	硬链接和软链接指向的inode的编号是一样的
    B、	可以建立空文件的软连接
    C、	linux操作系统可以对目录进行硬链接
    D、	硬链接指向inode节点
9、	在以太网中，一个数据帧从一个站点开始发送，到该数据帧完全到达另一个站点的总时间等于（）
    A、信号传播时延加上帧的发送时延
    B、信号传播时延减去帧的发送时延
    C、信号传播时延的两倍
    D、帧的发送时延的两倍
10、下面有关NAT的描述，说法错误的是？
	A、NAT是一种把内部私有网络地址（IP地址）翻译成合法网络IP地址的技术。
B、NAT的实现方式有三种，即静态转换Static Nat、动态转换Dynamic Nat和端口多路复用OverLoad。
	C、NAT可以有效的缓解了IP地址不足的问题
D、虚拟机里配置NAT模式，需要手工为虚拟系统配置IP地址、子网掩码，而且还要和宿主机器处于同一网段
11、下面提供 FTP 服务的默认 TCP 端口号是（ ）。
	A、21  B、23  C、25  D、80
12、为实现以 ADSL 方式接入 Internet ，至少需要在计算机中内置或外置的一个关键硬设备是（）？
A、	网卡 B、集线器 C、调制解调器 D、路由器
13、具有5个10M端口的集线器的总带宽可以达到()
	A、50M  B、10M  C、2M  D、100M
14、在一个对IP地址为192.168.30.2的设备的ARP请求分组中，目标地址是（ ）。
	A、FF-FF-FF-FF  B、192.168.30.1  C、192.168.30.255  D、FF-FF-FF-FF-FF-FF
15、下面哪个命令可以统计一个文件中"lbbxsxlz"出现的行数？
	A、vim "lbbxsxlz" 文件名 | wc –l  B、grep " lbbxsxlz" 文件名 | wc –l
	C、cat " lbbxsxlz " 文件名 | wc –l  D、ls  " lbbxsxlz " 文件名 | wc –l
16、下列命令能查找当前目录一个月(30天)以前大于100M的日志文件(.log)并删除
	A、find  . -name "*.log" –m time +30 –type f –size +100M |xargs rm –rf {} ;
	B、find  . -name "*.log" –mtime +30 –type f –size +100M |xargs rm –rf {} ;
	C、find  . -name "*.log" –mtime +30 –type –size 100M |xargs rm –rf {} ;
	D、find  . -name "*.log" –mtime +30 –type f –size 100M |xargs rm –rf {} ;
17、Linux什么情况下回发生page fault？
	A、系统可用内存不够时 B、所需访问虚拟内存未被装载
	C、当开始进行swap交换时 D、进程被挂起时
18、cp拷贝命令的-f参数含义为?
	A、拷贝目录 B、递归处理  C、显示执行过程 D、强制执行拷贝
19、下列不属于linux内核锁的一项是（）
    A、Semaphore  B、spinlock  C、seqlock  D、message
20、在OSI模型中，HTTP协议工作在第()层，交换机工作在第（）层。
	A、7 1  B、7 2  C、6 3 D、6 2
21、linux 创建文件的命令有（）
	A、ls  B、touch  C、cat  D、>  E、vi/vim
22、在Linux系统，关于硬链接的描述正确的是（）
	A、跨文件系统   B、不可以跨文件系统 
    C、为链接文件创建新的i节点  D、链接文件的i节点与被链接文件的i节点相同
23、如何查看当前Linux系统的状态,如CPU使用,内存使用,负载情况，下列描述正确的是？
	A、可以使用top命令分析CPU使用，内存使用，负载等情况
	B、可以使用free查看内存整体的使用情况
	C、可以使用cat /proc/meminfo查看内存更详细的情况
	D、可以使用cat /proc/buddinfo查看内存块详细的情况
24、下列关于makefile描述正确的有？
	A、makefile文件保存了编译器和连接器的参数选项
	B、主要包含了五个东西：显式规则、隐晦规则、变量定义、文件指示和注释
    C、默认的情况下，make命令会在当前目录下按顺序找寻文件名为“GNUmakefile”、“makefile”、“Makefile”的文件， 找到了解释这个文件
D、在Makefile不可以使用include关键字把别的Makefile包含进来
25、下列哪些可以用于Linux进程间通讯?
	A、UNIX套接字 B、pipe  C、fifo  D、信号量 E、文件锁 F 共享内存
