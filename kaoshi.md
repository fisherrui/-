# 单选题

(每题1分)

1, 如何快速切换到用户user1的家目录下? ( D )

```
A. cd @user1
B. cd #user1
C. cd &user1
D. cd ~user1
```

2, 如果快速切换到上一次所在的目录? ( B )

~~~powershell
A. cd @
B. cd -
C. cd &
D. cd ~
~~~

3, 下列哪条命令可以杀掉进程及其子进程? ( C )

~~~powershell
A.kill -9		
B.kill -1		
C.kill -15   	
D.kill -3
~~~

4, 下列哪条命令可以得到当前目录的路径? ( D )

~~~powershell
A. echo ${pwd}		
B. pwd |echo	
C. echo pwd		
D. echo $(pwd)
~~~

5, 哪个命令用来显示系统中各个分区中inode的使用情况？( A )

~~~powershell
A.df -i		
B.df -h		
C.df -H		
D.du -sh
~~~

6, 下面哪条命令可以把f1.txt复制为f2.txt? ( C )

~~~powershell
A. cp f1.txt | f2.txt
B. cat f1.txt | f2.txt
C. cat f1.txt > f2.txt
D. copy f1.txt | f2.txt
~~~

7, 下面哪种写法表示如果cmd1成功执行，则执行cmd2命令？（A )

~~~powershell
A. cmd1 && cmd2
B. cmd1 | cmd2
C. cmd1 ; cmd2
D. cmd1 || cmd2
~~~

8, 哪条命令用于查找文件属于哪个rpm包? ( C )

~~~powershell
A. rpm -qa
B. rpm -qc
C. rpm -qf
D. rpm -ql
~~~

9, 如果有一个文件在/etc目录下,只有5个字节大小,请问下面哪条命令可以将其找出来? ( A )

~~~powershell
A. find /etc -size -2b
B. find /etc -size +4k
C. find /etc -size -5c
d. find /etc -size +1M
~~~

10, 下面哪一种服务不需要加ssl协议来实现安全传输? ( C )

~~~powershell
A. http
B. ftp
C. dns
D. email
~~~

11, 我想共享一些资料文件给windows客户端下载,下面哪个服务不适合?  ( C )

~~~powershell
A. httpd
B. samba
C. nfs
D. ftp
~~~

12, 我想共享一个目录给多个用户访问,还要对不同用户的访问权限实现精细控制,下面哪个服务最适合? ( B )

~~~powershell
A. httpd
B. samba
C. nfs
D. ftp
~~~

13, 下面哪个服务使用防火墙控制无效? ( A )

~~~powershell
A. crond
B. ftp
C. nfs
D. httpd
~~~

14, 哪个选项不是python语言保留关键字? ( B )

~~~powershell
A. pass
B. do
C. except
D. while
~~~

15, 下面哪个工具不能备份mysql的innodb存储引擎的表? (  A )

~~~powershell
A. mysqlhotcopy 
B. mysqldump
C. xtrabackup
D. mysql enterprise backup
~~~

16, 公司开发了一个java写的程序, 使用下面哪个服务可以运行? ( D )

~~~powershell
A. lnmp
B. lamp
C. pycharm
D. tomcat
~~~

17, 下面哪个软件不能做负载均衡调度器? （G )

~~~powershell
A. nginx
B. haproxy
C. lvs
D. keepalived
E. apache
F. dns
G. heartbeat
~~~

18, 使用nginx负载均衡两个web服务器,下面哪种存储技术不能实现两个web服务的数据同步? ( D )

~~~powershell
A. rsync
B. drbd
C. nfs
D. iscsi
E. glusterfs
~~~

19, 我现在有4个硬盘，2个250G, 2个500G,如果做raid10的话,请问能存放的最大有效数据为多大?（B）

~~~powershell
A. 250G           
B. 500G
C. 750G
D. 1000G
~~~

20, 下面哪个软件不能做配置自动化工具? ( C )

~~~powershell
A. ansible
B. puppet
C. cacti
D. saltstack
~~~




# 多选题

(选项个数不定，每题2分)

python的数据类型里，下面哪种类型没有下标? ( D,E )

~~~powershell
A. str
B. list
C. tuple
D. dict
E. set
~~~

下列哪些软件能实现高可用? ( A,B,C,E )

~~~powershell
A. heartbeat
B. keepalived
C. RHCS
D. lvs
E. pacemaker
~~~

mysqlAB复制的架构中,下面哪种架构可以实现? ( A,B,C,D,E,F )    说明:mysql5.7有多源复制（多主一从)

~~~powershell
A. 一主一从
B. 一主多从
C. 多主一从
D. 双主
E. 级联
F. 环形
~~~

下面哪些属于SQL语句的分类? ( A,B,D,E)

~~~powershell
A. DCL  grant revoke
B. DDL  create drop alter truncate
C. DEL  
D. DML  insert update delete
E. DQL  select
~~~

下面哪些是nginx支持的负载均衡调度算法? ( A,B,C,D,G )

~~~powershell
A. rr
B. wrr
C. ip_hash
D. url_hash
E. lc
F. sh
G. fair
~~~

下面哪些服务支持PAM验证? ( A,B,D )

~~~powershell
A. vsftpd
B. sshd
C. zabbix
D. samba
E. ansible
~~~





# 简答题

如何把/etc/skel/目录里以.开头的隐藏文件(包括隐藏的子目录,)拷到/test/目录,请写出拷贝命令 (3分)

~~~powershell
# cp /etc/skel/.[a-Z]*  /test/ -rf
# cp -r /etc/skel/. /test/
~~~



centos7服务器上跑了httpd服务,除了systemctl stop httpd可以关闭服务外,还可以用什么命令找到所有相关进程并杀掉?  (3分)

~~~powershell
ps -ef |grep httpd |grep -v grep |awk '{print $2}' |xargs kill -9
pgrep httpd |xargs kill -9
killall httpd
pkill httpd
skill httpd
~~~



简述raid0,raid1,raid5三种raid方式的区别与优缺点. (3分)

~~~powershell
raid0 条带 提高数据读写性能 但一个盘挂掉，整个raid会挂掉,也就是说没有磁盘高可用性  磁盘利用率100%
raid1 镜像 有磁盘高可用性，但没有提高数据读写性能   磁盘利用率50%
raid5 即提高了读写性能，也有数据可靠性，是生产环境中常用的raid级别		磁盘利用率n-1/n
~~~



下图的内网服务器不指网关，在中间的防火墙机器上写iptables的NAT规则使client能够访问内网服务器的80端口.(4分)

```powershell

		client		10.1.1.11
		  |
		  |
		  |	eth0	10.1.1.12
		防火墙
		  |	eth1	192.168.100.12
		  |
		  |
		内网服务器	192.168.100.13
```

~~~powershell
答:
SIP:10.1.1.11	    	DIP:10.1.1.12
通过防火墙,做DNAT
SIP:10.1.1.11	     	DIP:192.168.100.13
到达内网服务器，返回
SIP:192.168.100.13    	DIP:10.1.1.11
通过网关指向192.168.100.12，回到防火墙，自动SNAT
SIP:10.1.1.12	     	DIP:10.1.1.11


SIP:10.1.1.11	     	DIP:10.1.1.12
通过防火墙,做DNAT和SNAT
SIP:192.168.100.12    	DIP:192.168.100.13
到达内网服务器，返回
SIP:192.168.100.13    	DIP:192.168.100.12
直接通过同网段路由回到防火墙，自动SNAT和DNAT
SIP:10.1.1.12	     	DIP:10.1.1.11

# iptables -A POSTROUTING -p tcp --dport 80 -o eth1  -j SNAT --to 192.168.100.12
# iptables -A PREROUTING  -p tcp --dport 80 -i eth0  -j DNAT --to 192.168.100.13
# echo 1 > /proc/sys/net/ipv4/ip_forward
~~~



负载均衡集群需要关注被调度的web服务器的session一致性,请写出下列架构能使用什么算法或什么技术能实现被调度的服务的session一致? (5分)

~~~powershell
架构1:nginx调度多台nginx_web服务器
答: nginx的ip_hash算法

架构2:nginx调度多台tomcat
答: nginx的ip_hash算法
    tomcat的session复制集群
    memcached-session-manager
    
架构3:haproxy调度多台nginx_web服务器
答: haproxy的source算法
    使用cookie
    使用stick table
~~~





# 程序题

(用shell或python都行，每题5分)

1, 随意指定一个存在的目录,判断此目录内的可用空间是否大于3G

~~~powershell
#!/bin/bash

read -p "输入你要安装的路径:" installpath
if [ ! -d $installpath ];then
	echo "你输入的安装路径不是一个目录;重试"
	sh $0
	exit 1
fi

size=`df -P $installpath |tail -1 |awk '{print $4}'`

if [ $size -lt 3000000 ];then
	echo "你输入的安装路径空间不够，退出"
	exit 2
else
	echo "空间OK，继续安装"
fi
~~~

2, 找出字符长度大于5，并且包含数字的用户名，显示用户名，并统计个数

~~~powershell
awk -F: 'BEGIN {sum=0} length($1)>5 && $1~"[0-9]" {print $1;sum=sum+1}END {print "个数为:"sum}' /etc/passwd
~~~

3, 建立一百个用户，要求:

* 这一百个用户分别为usera1-usera10, userb1-userb10, userc1-userc10, ......一直到userj1-userj10
* 密码与用户名一致
* usera1到userj10这100个用户分别对应的uid和gid为1600到1699，也就是说usera1的uid和gid都为1600,usera2的都为1601，以此类推

~~~powershell
for i in {a..j}
do
        for j in {1..10}
        do
              xxxxxxxxxxxxxxx
        done
done


a=('a' 'b' 'c' 'd' 'e' 'f' 'g' 'h' 'i' 'j')
num=1600

for a in ${a[*]}
do
	for((i=1;i<=10;i++))
	do
		xxxxxxxxxxxxxx
	done
        
done


#!/bin/bash
ID=1600
for i in {a,b,c,d,e,f,g,h,i,j}
do
     for ((j=1;j<=10;j++))
     do
         groupadd -g $ID user$i$j
         useradd -g $ID -u $ID user$i$j
         echo user$i$j | passwd --stdin user$i$j  & >/dev/null
         let ID++
     done
done
~~~

4, 文本转换

~~~powershell
一个文本文件内容如下
# cat 1.txt
aaAAaa bbbbbb 111111 
222222 CCCCCC DdDdDd
eEeEeE 333333 FFFfff
GGGGgg 444444 hhHHHH
iiiIII JJjjJj 555555

将其结果变为:
aaaaaa bbbbbb
cccccc dddddd
eeeeee ffffff
gggggg hhhhhh
iiiiii jjjjjj



cat  1.txt  |sed 's/[0-9]//g' |awk '{print tolower($1),tolower($2)}'
~~~

5, 找出每天18：30之前下班的打卡记录

~~~powershell
# cat 2.txt
张三  2013-7-01 18:19:28
张三  2013-7-02 17:58:45
张三  2013-7-03 22:41:47
张三  2013-7-04 22:15:23
张三  2013-7-05 19:12:27
张三  2013-7-06 19:03:09
张三  2013-7-07 19:09:44
张三  2013-7-08 19:04:45
张三  2013-7-09 18:39:28
张三  2013-7-10 18:24:48
张三  2013-7-11 18:58:21
张三  2013-7-12 18:36:22
张三  2013-7-13 19:23:46
张三  2013-7-14 19:02:41
张三  2013-7-15 19:00:09
张三  2013-7-16 18:36:13
张三  2013-7-17 18:36:40
张三  2013-7-18 19:00:00
张三  2013-7-19 18:31:18
张三  2013-7-20 18:44:01
张三  2013-7-21 18:37:12
张三  2013-7-22 18:29:33


# cat 2.txt |awk -F"[ :]*" '$3==18 && $4<30 ||$3< 18 {print $0}'

# cat 2.txt |awk -F"[ :]*" '$3$4<1830 {print $0}'

# cat 2.txt |awk '$3<"18:30:00" {print $0}'  --时间直接比较是可以的，但是如果你小时为个位数（比如9:00:00，你应该要写成09:00:00才可以直接比)
~~~

6. 假设9点整上班，算出下面这几天这几个人分别迟到多少次，和扣多少钱（一次扣10块)

```powershell
# cat 3.txt
张三 2013-8-25 09:19:28
李四 2013-8-25 08:58:45
王五 2013-8-25 08:41:47
马六 2013-8-25 09:12:52
田七 2013-8-25 09:01:47
张三 2013-8-24 08:49:28
李四 2013-8-24 08:54:45
王五 2013-8-24 09:11:47
马六 2013-8-24 09:02:52
田七 2013-8-24 09:04:47
张三 2013-8-23 09:29:28
李四 2013-8-23 08:57:45
王五 2013-8-23 08:41:47
马六 2013-8-23 09:08:52
田七 2013-8-23 09:09:47
张三 2013-8-22 09:24:28
李四 2013-8-22 09:16:45
王五 2013-8-22 09:11:47
马六 2013-8-22 08:52:52
田七 2013-8-22 08:44:47

# awk '$3>"09:00:00" {print $1}' 3.txt  |sort |uniq -c |awk 'BEGIN{print "迟到员工姓名\t罚款金额"}{print $2"\t\t"$1*10"元"}'
迟到员工姓名	罚款金额
张三		30元
李四		10元
王五		20元
田七		30元
马六		30元
```

7. 写一个采集内存的脚本，采集指标为内存总量，内存已使用，内存未使用（python的话使用psutil模块），最后print打印出采集的数据(要求1秒钟打印一次)。

~~~powershell
import psutil
import time

def mem_info():
    time.sleep(1)
    mem_obj = psutil.virtual_memory()
    swap_obj = psutil.swap_memory()

    print """
    ===============物理内存监控===================
    内存总量：%.2f M
    内存已使用： %.2f M
    内存未使用：%.2f M
    
    """ %(mem_obj.total/1024/1024, mem_obj.used/1024/1024, mem_obj.free/1024/1024)
    
    
mem_info()


#!/bin/bash
while(true)
do
free -m |awk -F' '  'NR==2{print$2,$3,$7}'
sleep 1
done
~~~





# 综合题

(15分)

用ansible的playbook或者saltstack的sls文件实现下面zabbix服务器的安装过程(有些地方不好写playbook或sls文件的可以部分用shell替代):

~~~powershell
1，添加yum仓库
# vim /etc/yum.repos.d/zabbix.repo
[zabbix]
name=zabbix
baseurl=http://repo.zabbix.com/zabbix/3.4/rhel/7/x86_64/
enabled=1
gpgcheck=0

2，安装zabbix和mariadb数据库
# rpm -ivh iksemel-1.4-6.el7.x86_64.rpm			注意这个包不在仓库内
# yum install epel-release
# yum install zabbix-server-mysql zabbix-web-mysql mariadb-server

3，在mysql(mariadb)里建立存放数据的库并授权，然后导入zabbix所需要用的表和数据
# systemctl restart mariadb.service
# systemctl enable mariadb.service


# mysql
MariaDB [(none)]> create database zabbix default charset utf8;
MariaDB [(none)]> grant all on zabbix.* to zabbix@'localhost' identified by '123';
MariaDB [(none)]> flush privileges;
MariaDB [(none)]> quit

4，导入表数据
# zcat /usr/share/doc/zabbix-server-mysql-3.4.15/create.sql.gz |mysql -u zabbix -p123 zabbix

5，配置zabbix主配置文件，并启动服务,确认端口
# vim /etc/zabbix/zabbix_server.conf
ListenPort=10051
DBHost=localhost
DBName=zabbix
DBUser=zabbix
DBPassword=123						--修改密码
DBSocket=/var/lib/mysql/mysql.sock 	--这里默认的socket路径不对，改成我这个路径
ListenIP=0.0.0.0

# systemctl restart zabbix-server
# systemctl enable zabbix-server

6,配置zabbix的httpd子配置文件,并启动httpd
[root@zabbixserver ~]# vim /etc/httpd/conf.d/zabbix.conf

20 php_value date.timezone Asia/Shanghai

# systemctl restart httpd 
# systemctl enable httpd
~~~



**答案:**(我这里用saltstack来实现的)

~~~powershell
在master上创建zabbix管理目录
# mkdir /srv/salt/zabbix

此目录准备的文件如下:
# ls /srv/salt/zabbix	
zabbix.repo							--yum配置文件(配置好zabbix3.4的公网源)
iksemel-1.4-6.el7.x86_64.rpm		--iksemel依赖包
zabbix_server.conf					--zabbix_server配置文件(将相应的选项配置好)
httpd_zabbix.conf					--httpd的zabbix子配置文件(将时区修改好)
mysql.sh							--创建mysql库，授权，导入mysql数据的脚本


mysql.sh脚本内容如下
# cat /srv/salt/zabbix/mysql.sh   
#!/bin/bash

mysql << EOF 
create database zabbix default charset utf8;
grant all on zabbix.* to zabbix@'localhost' identified by '123';
flush privileges;
quit
EOF

zcat /usr/share/doc/zabbix-server-mysql-3.4.*/create.sql.gz |mysql -u zabbix -p123 zabbix
~~~



~~~powershell
# vim /srv/salt/zabbix.sls

yum-config:
  file.managed:
    - name: /etc/yum.repos.d/zabbix.repo
    - source: salt://zabbix/zabbix.repo

iksemel-copy:
  file.managed:
    - name: /tmp/iksemel-1.4-6.el7.x86_64.rpm
    - source: salt://zabbix/iksemel-1.4-6.el7.x86_64.rpm

rpm-install-iksemel:
 cmd.run:
   - name:
        rpm -i /tmp/iksemel-1.4-6.el7.x86_64.rpm
   - user: root
   
epel-install:
  pkg.installed:
    - names:
      - epel-release
      
zabbix-install:
  pkg.installed:
    - names:
      - zabbix-server-mysql
      - zabbix-web-mysql
      - mariadb-server

mariadb-run:
  service.running:
      - name: mariadb
      - enable: True
   
mysql_script_execute:
 cmd.script:
   - source: salt://zabbix/mysql.sh
   - user: root

zabbix-config:
  file.managed:
    - name: /etc/zabbix/zabbix_server.conf
    - source: salt://zabbix/zabbix_server.conf
    
httpd-config:
  file.managed:
    - name: /etc/httpd/conf.d/zabbix.conf
    - source: salt://zabbix/httpd_zabbix.conf   
    
zabbix-server-run:
  service.running:
      - name: zabbix-server
      - enable: True
      
httpd-run:
  service.running:
      - name: httpd
      - enable: True
~~~



