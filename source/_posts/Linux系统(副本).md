# Linux系统

## **常见单词**

disabled  不可用的
enabled   可用的
vaild      有效的
invaild      无效的
available    可获取的
unavailable 不可获取的
synchronize   同步
version  版本
probe 探查
primary 主要的
extend 拓展
logical    逻辑的
quota 配额
swap 交换分区
defaults 默认值
volume 体积、卷、容量 
lvm(logical volume management)  逻辑卷管理 
physics  物理学  /ˈfɪzɪks/
limits 限度、范围
scan	扫描
mapper  映射
ethernet	以太网（构建局域网）
broadcast  广播地址
virtualization   虚拟化的
route	路线
destination   目标
protocol 	 协议
process	进程
command	 命令
domian 域
generate 生成 ssh -keygen
private  私人的
synchronize  同步
authorize  授权

## **远程文件服务器**

[centos7.9]
name=centos7.9
baseurl=file:///mnt
enanled=1
pgpcheck=0
 =ftp://192.168.56.138/centos7u2

## 源码安装htop

1、安装autoconf（安装m4）
报错-->安装perl
2、执行autoconf生成configure后，执行./configure
报错-->configure: error: cannot find install-sh, install.sh, or shtool in "." "./.." "./../.."
3、安装automake（检查是否安装成功automake --version）
4、安装libtool
5、./configure 报错-->configure: error: You may want to use --disable-unicode or install libncursesw.
6、处理5报错后，执行./configure.