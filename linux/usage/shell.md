##文件
#####搜索文件
1.whereis
在数据库 /var/lib/mlocate/ 中查询（linux系统自动创建的，包含本地所有文件的信息，每天自动执行updatedb更新一次）
快速但不准确，只能用于搜索可执行文件，联机帮助文件和源代码文件

2.locate
使用whereis相同的数据库，但比whereis更全面。
locate ls,只要文件名或路径中包含ls，就能搜出来。
如要精确搜索可以 locate -b "\ls"

3.which
只要$PATH环境变量包含的路径下搜索

4.type
本来是用来判断一个命令是否属于shell内置的。加上-p参数相当于which

5.find
简单举例
find / -mtime 3 => 3天前那天发生变化的文件
find / -mtime -3 => 3天以内发生变化的文件
find / -mtime +3 => 3天以前发生变化的文件
find / -mtime -1  -exec ls -al {} \;  => "{}" 站位， "\" 转义 ; 因为；在bash shell里有特殊含义

其他更多的用法在使用中慢慢积累

#####创建tar包
z代表gz， j代表bz2， J代表xz
tar -zcvf filename.tar.gz files
tar -jcvf filename.tar.bz2 files
tar -Jcvf filename.tar.xz files
压缩比 gz<bz2<xz
压缩速度 gz>bz2>xz
#####解压
.tar文件 tar -vxf filename.tar
其他，把创建时参数c换成x

另外，还有dump和restore一对儿备份还原工具，能够对文件进行打包和解包。
除此之外，还有cpio,可以备份任何东西，也可以打包。linux系统初始化镜像文件initrd就是cpio制作的。
它所打包的文件名不是利用命令选项提供，而是通过标准输入传入。而最终的产生的打包文件，也不是直接输出到磁盘而是输出到标准输出中。
$find ... | cpio -ocB > filename
解压时也要通过标准输入中读数据
cpio -idc < filename

#####进程
1、linux Kill多个进程的案例:干掉nginx所有进程

经常需要Kill多个进程，如果这些进程有共同的特点，就可以用一条命令Kill掉它们。比如清除Nginx所有进程：
ps -aux|grep nginx|grep -v grep|cut -c 9-15|xargs kill -9

管道符“|”用来隔开两个命令，管道符左边命令的输出会作为管道符右边命令的输入

下面说说用管道符联接起来的几个命令：

“ps -aux”是linux里查看所有进程的命令。这时检索出的进程将作为下一条命令“grep nginx”的输入。

“grep nginx”的输出结果是，所有含有关键字“nginx”的进程，这是Nginx进程的共同特点。

“grep -v grep”是在列出的进程中去除含有关键字“grep”的进程。

“cut -c 9-15”是截取输入行的第9个字符到第15个字符，而这正好是进程号PID。

“xargs kill -9”中的xargs命令是用来把前面命令的输出结果（PID）作为“kill -9”命令的参数，并执行该命令。

kill -9”会强行杀掉指定进程，这样就成功清除了nginx的所有远程连接进程。其它类似的任务，只需要修改“grep nginx”中的关键字部分就可以了。

2、多个进程如果是相同的进程名可以使用pkill命令

"pkill"命令允许使用扩展的正则表达式和其它匹配方式。你现在可以使用应用的进程名kill掉它们，而不是使用PID。例如，要kill掉nginx，只需要运行命令：
pkill  nginx

3、多个进程如果是相同的进程名可以使用Killall命令

killall同样使用进程名替代PID，并且它会kill掉所有的同名进程。例如，如果你正在运行多个nginx的实例，可以用命令把它们全部kill掉：
killall  nginx

