# **linux系统**

## **常见单词**

invalid      无效的   
available      可获取的
unavailable   不可获取的
permission  请求  
denied         被拒绝
operation     操作
permit     允许
alias    别名
extract	提炼 tar -xf
query 	查询
pattern	 模式
apend	 附加
dependence	  依赖
primary 	主要的
extended   拓展
logical  	逻辑的
version  	版本
enterprise   企业的epel库  extra Packages for enterprise Linux
defaults  	默认值
sitcky bit（SBIT）粘滞位
probe  	探测
device  	设备
synchronize    同步
swap	交换
quota  	配额
edit 	编辑
resource  资源
verbose 	详细信息
spare	备用的
transmission    传输
protocol          协议
broadcast	     广播
ethernet	以太网（构建局域网）
Destination   目的（目标网段）
gateway   网关
method	方法/ ˈmeθ.əd /
manual	手动的 / ˈmæn.ju.əl /
detect	探测
port	端口
stat	统计数据
Memory	内存
signal	信号
interrupt	中断
terminate	  终止
foreground  前景（fg命令-编号）
multi-user.target 多用户模式/字符模式
graphical    图像化的
domian 域
localdomain   本地域
syntax   ˈsinˌtaks   语法
authentication /ôˌTHen(t)iˈkāSH(ə)n/  验证
phrase / freɪz /   短语     passphrase  
authorize 授权
export 输出
anonymous /əˈnɑː.nə.məs/ 匿名的
squash   压缩
utils 实用程序  nfs服务器
option 选项
code 	代码
node 	节点
preview	/ ˈpriː.vjuː / 预览
grant	授权
forbidden	   禁止
administrator 管理员
expire   到期
satisfy /ˈsæt̬.ɪs.faɪ/ 满足
identify 过去式 identified  识别，确定，发现
conver 转换  iconv -f 原编码 -t 目标编码 文件
daemon 守护进程  mysqld
mysql-communication-common 沟通
alter	改变
policy     政策，规则
select	选择
privileges	  特权
validate_password_policy  核实，证实
programmer  程序员
confirm /kənˈfərm/  确认
convention 惯例，习俗
refactor  重构
docstring  注释
split 分开 vim多窗口vs水平分屏，sp竖直分屏
registry  /ˈrejəstrē/ 注册表	
recursive   /rəˈkərsiv/ 递归的
branch	分支
conflict  冲突
customize   定制化
interperter /inˈtərprədər/ 编译器
confirm  /kənˈfərm/   确认	
initiate  /ɪˈnɪʃ.i.eɪt/  发起、开始

## **Linux基础**

### **正向解析**

（DNS文件- bind bind-chroot）

```shell
options {
	directory "/var/named";
};
zone "uplooking" {
	type master;
	file "uplooking.com.zone";
	allow-transfer { 192.168.247.7; };
};
zone "247.168.192.in-addr.arpa" {
	type master;
	file "192.168.247.zone";
};
```

### **反向解析**

```shell
options {
	directory "/var/named";
}
zone "uplooking.com" {
	type slave;
	masters { 192.168.247.6; };
	file "slaves/uplooking.com.zone";
}
```

### **apache网站设置**

```shell
Allowoverride AuthConfig
AuthType Basic
AuthName "Restricted page"
AuthUserFile "/etc/name/.webuser"
Require vaild-user
```

```shell
<VirtualHost 121.41.74.169:80>
	ServerName www.a.org
	DocumentRoot  /var/www/html/.org
	CustomLog /var/log/httpd/a.org/access_log
	ErrorLog /var/log/httpd/a.org/error_log
</VirtualHost>
```

针对CentOS6 设置关闭NetworkManager
[root@localhost ~]service NetworkManager stop 
[root@localhost ~]# chkconfig NetworkManager off

### **URL重定向**

```shell
RewriteEngin On
RewriteCond %{HTTP_HOST} ^www.sh.com
RewriteRule ^/(.*)  https://www.sh.com [L]
```

[apache如何设置http自动跳转到https](https://blog.csdn.net/p312011150/article/details/81977282)

### **常见端口**

21:ftp
22:ssh
23:telnet
25:smtp
53:DNS
80:http 443:https
1433:mysql server
3306:MySQL

### **vim常见设置**

bash_profile  环境变量
bash_logout
bashrc  alias别名
自启动 /etc/rc.d/rc.local

set ts=4 vim 设置制表键空格数，默认8个空格，不同系统（2或4位）
set expandtab 将制表键tab转为空格 /expand 扩张
set autoindent 设置换行后自动对齐

### **虚拟机网卡设置**

DEVICE=ens33
NAME=ens33
ONBOOT=yes
NETBOOT=yes
BOOTPROTO=dhcp/none
IPADDR=192.168.56.156
PREFIX=24
GATEWAY=192.168.56.2
DNS=192.168.56.2
TYPE=Ethernet

### **常见文件服务器**

samba 安装包 samba-client
ftp 
nfs 安装包 rpcbind  nfs-utils

autoconf 自动配置
automake
autoreconf -ivf

### **设置ftp文件共享**

[centos7.9]
name=centos7.9
baseurl=file:///mnt   
baseurl=ftp://192.168.56.139/centosu2
enabled=1
gpgcheck=0

### **回环地址**

127.0.0.1        回环地址，亦称回送地址，指本机地址
127.127.1.0    ntp服务器地址

10.145.129.20
255.255.248.0

10.145.10000001.20
255.255.11111000.00000000
10.145.10000000.0
网络地址 10.145.128.0

10.145.10000111.11111111
广播地址 10.145.135.255

## **安装nodejs**

### **安装tldr**

安装nodejs（包含npm工具，可独立安装）
install -g tldr（中国淘宝镜像npm config set registry https://registry.npm.taobao.org/）

### **安装pylint**

python3自带安装工具pip3--检测脚本评分命令pylint
安装   pip3 install pylint
用法   pylint <文件>

### **hexo搭建博客**

npm install -g hexo-cli 
hexo init blog（创建博客项目文件，用到git）
cd blog
npm install (安装json依赖项，文件package.json,Python环境也有此依赖项文件)  hexo generate或 hexo g   生成js文件
hexo server -p 80 > hexo.log 2> hexo-error.log & 

## **Typora使用**

### **有序列表**

数字加. 加空格

1. 第一点
2. 第二点
3. 

反引号``表示特殊符号的标记或者一行代码的标记

` a > b`

加粗字体 ** 或者快捷键crtl + b  ；表格的快捷键crtl + t

### 无序列表

横线+空格

- 

### 引入图片/链接

![图片的名称]()   

注意：本地地址的路径，对应的图片一定要存在

超链接  
`[链接名](链接地址)`

[我赢职场](https://www.wyzc.com/)  [阿里云开源镜像](https://mirrors.aliyun.com/repo/)  常见的rpm包网站：[Rpm](https://rpmfind.net/)   [Pkgs](https://pkgs.org/)
1.[配置-在 ac-aux 中找不到 install-sh、install.sh 或 shtool](https://askubuntu.com/questions/27677/cannot-find-install-sh-install-sh-or-shtool-in-ac-aux)]
2.[没有configure文件时如何编译安装软件包？](https://www.jianshu.com/p/b97d3.b7c9c915) 
3.[源码安装最坑的是什么](https://cloud.tencent.com/developer/article/1563519) 
4.[Apache之Rewrite和RewriteRule规则梳理以及http强转https的配置总结](https://blog.51cto.com/u_6215974/4937189)
5.[Python菜鸟教程](https://www.runoob.com/python3/python3-tutorial.html)
6.[千锋教育](https://video.mobiletrain.org/video/4/20)
7.Stack overflow(简称So)  [栈溢出](https://stackoverflow.com/)





