#####文件
##搜索文件
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

##创建tar包
z代表gz， j代表bz2， J代表xz
tar -zcvf filename.tar.gz files
tar -jcvf filename.tar.bz2 files
tar -Jcvf filename.tar.xz files
压缩比 gz<bz2<xz
压缩速度 gz>bz2>xz
##解压
.tar文件 tar -vxf filename.tar
其他，把创建时参数c换成x

另外，还有dump和restore一对儿备份还原工具，能够对文件进行打包和解包。
除此之外，还有cpio,可以备份任何东西，也可以打包。linux系统初始化镜像文件initrd就是cpio制作的。
它所打包的文件名不是利用命令选项提供，而是通过标准输入传入。而最终的产生的打包文件，也不是直接输出到磁盘而是输出到标准输出中。
$find ... | cpio -ocB > filename
解压时也要通过标准输入中读数据
cpio -idc < filename


