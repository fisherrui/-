### 1. 生成磁盘使用情况的日志文件

```python
#!/usr/bin/env python
#!coding=utf-8

import time
import os

new_time = time.strftime('%Y-%m-%d')
disk_status = os.popen('df -h').readlines()
str1 = ''.join(disk_status)
f = file(new_time+'.log','w')
f.write('%s' % str1)
f.flush()
f.close()


```



### 2. 探测Web服务质量

```python
#!/usr/bin/python
# -*- coding: UTF-8 -*-
# 该脚本可以定位访问web页面的服务质量
# 通过Python下的pycurl模块来实现定位
# 它可以通过调用pycurl提供的方法，来探测Web服务质量
# 比如了解相应的HTTP状态码、请求延时、HTTP头信息、下载速度等

import os
import time
import sys
import pycurl

# 探测目标URL
URL = "http://www.baidu.com" 

# 创建一个Curl对象
c = pycurl.Curl()
# 定义请求的URL变量
c.setopt(pycurl.URL, URL)
# 定义请求连接的等待时间
c.setopt(pycurl.CONNECTTIMEOUT, 5)
# 定义请求超时时间
c.setopt(pycurl.TIMEOUT, 5)
# 屏蔽下载进度条
c.setopt(pycurl.FORBID_REUSE, 1)
# 指定HTTP重定向的最大数为1
c.setopt(pycurl.MAXREDIRS, 1)
# 完成交互后强制断开连接，不重用
c.setopt(pycurl.NOPROGRESS, 1)
# 设置保存DNS信息的时间为30秒
c.setopt(pycurl.DNS_CACHE_TIMEOUT,30)

# 创建一个文件对象，以“wb”方式打开，用来存储返回的http头部及页面的内容
indexfile = open(os.path.dirname(os.path.realpath(__file__))+"/content.txt", "wb")
# 将返回的HTTP HEADER定向到indexfile文件
c.setopt(pycurl.WRITEHEADER, indexfile)
# 将返回的HTML内容定向到indexfile文件
c.setopt(pycurl.WRITEDATA, indexfile)

# 捕捉Curl.perform请求的提交，如果错误直接报错退出
try:
    c.perform()
except Exception,e:
    print "连接错误"
    indexfile.close()
    c.close()
    sys.exit()

# DNS解析所消耗的时间
NAMELOOKUP_TIME = c.getinfo(c.NAMELOOKUP_TIME)
# 建立连接所消耗的时间
CONNECT_TIME = c.getinfo(c.CONNECT_TIME)
# 从建立连接到准备传输所消耗的时间
PRETRANSFER_TIME = c.getinfo(c.PRETRANSFER_TIME)
# 从建立连接到传输开始消耗的时间
STARTTRANSFER_TIME = c.getinfo(c.STARTTRANSFER_TIME)
# 传输结束所消耗的总时间
TOTAL_TIME = c.getinfo(c.TOTAL_TIME)
# 返回HTTP状态码
HTTP_CODE = c.getinfo(c.HTTP_CODE)
# 下载数据包的大小
SIZE_DOWNLOAD = c.getinfo(c.SIZE_DOWNLOAD)
# HTTP头部大小
HEADER_SIZE = c.getinfo(c.HEADER_SIZE)
# 平均下载速度
SPEED_DOWNLOAD = c.getinfo(c.SPEED_DOWNLOAD)


print "HTTP状态码：%d" %HTTP_CODE
print "DNS解析时间：%.2f ms"%(NAMELOOKUP_TIME*1000)
print "建立连接时间：%.2f ms" %(CONNECT_TIME*1000)
print "准备传输时间：%.2f ms" %(PRETRANSFER_TIME*1000)
print "传输开始时间：%.2f ms" %(STARTTRANSFER_TIME*1000)
print "传输结束总时间：%.2f ms" %(TOTAL_TIME*1000)
print "下载数据包大小：%d bytes/s" %(SIZE_DOWNLOAD)
print "HTTP头部大小：%d byte" %(HEADER_SIZE)
print "平均下载速度：%d bytes/s" %(SPEED_DOWNLOAD)
indexfile.close()
c.close()


"""
HTTP状态码：%d 
DNS解析时间：%.2f ms 
建立连接时间：%.2f ms 
准备传输时间：%.2f ms 
传输开始时间：%.2f ms 
传输结束总时间：%.2f ms 
下载数据包大小：%d bytes/s 
HTTP头部大小：%d byte 
平均下载速度：%d bytes/s 
""" %(HTTP_CODE, NAMELOOKUP_TIME*1000, CONNECT_TIME*1000, PRETRANSFER_TIME*1000, STARTTRANSFER_TIME*1000, TOTAL_TIME*1000, SIZE_DOWNLOAD, HEADER_SIZE, SPEED_DOWNLOAD)

```



### 3. 发送邮件告警

```python
import smtplib
from email.mime.text import MIMEText
'''
发送邮件函数，默认使用163smtp
:param mail_host: 邮箱服务器，16邮箱host: smtp.163.com
:param port: 端口号,163邮箱的默认端口是 25
:param username: 邮箱账号 xx@163.com
:param passwd: 邮箱密码(不是邮箱的登录密码，是邮箱的授权码)
:param recv: 邮箱接收人地址，多个账号以逗号隔开
:param title: 邮件标题
:param content: 邮件内容
:return:
'''
 
def send_mail(username, passwd, recv, title, content, mail_host='smtp.163.com', port=25):
  msg = MIMEText(content)  # 邮件内容
  msg['Subject'] = title   # 邮件主题
  msg['From'] = username   # 发送者账号
  msg['To'] = recv      # 接收者账号列表
  smtp = smtplib.SMTP(mail_host, port=port)   # 连接邮箱，传入邮箱地址，和端口号，smtp的端口号是25
  smtp.login(username, passwd)          # 登录发送者的邮箱账号，密码
  # 参数分别是 发送者，接收者，第三个是把上面的发送邮件的 内容变成字符串
  smtp.sendmail(username, recv, msg.as_string())
  smtp.quit() # 发送完毕后退出smtp
  print('email send success.')
 
if __name__ == '__main__':
  email_user = 'xxxx@163.com' # 发送者账号
  email_pwd = 'xxxxx' # 发送者密码,授权码
  maillist = 'xxxx@qq.com'
  title = '测试邮件标题'
  content = '这里是邮件内容'
  send_mail(email_user, email_pwd, maillist, title, content)
```





### 4. 收集系统信息

采集系统信息包括了CPU，内存，磁盘，网络等。结合自身情况。

psutil模块是一个跨平台的获取进程和系统应用情况（CPU，内存，磁盘，网络，传感器）的库。该模块用于系统监控、限制进程资源和运行进程的管理等方面。

```python
(1) CPU信息
psutil.cpu_count() # CPU逻辑数量
psutil.cpu_count(logical=False) # CPU物理核心
psutil.cpu_percent() # CPU当前使用率

(2) 内存信息
mem = psutil.virtual_memory() # 实例化内存对象
mem.total  # 系统总计内存
mem.used  # 系统已经使用内存
mem.free # 系统空闲内存
psutil.swap_memory() # swap内存信息

(3) 硬盘信息
psutil.disk_usage('/')

(4) 网络信息
psutil.net_io_counters(pernic=True)
```



#### 4.1 CPU利用率采集脚本

```python
#!/bin/python
#coding:utf-8

import psutil
import time

while True:
    time.sleep(1)
    cpu_liyonglv = psutil.cpu_percent()
    print "当前cpu利用率：\033[1;31;42m%s%%\033[0m"%cpu_liyonglv
```

#### 4.2 内存使用率和用户采集脚本

```python
#!/bin/python
#coding:utf-8

import psutil
import datetime

free = str(round(psutil.virtual_memory().free / (1024.0 * 1024.0 * 1024.0), 2))
total = str(round(psutil.virtual_memory().total / (1024.0 * 1024.0 * 1024.0), 2))
memory = int(psutil.virtual_memory().total - psutil.virtual_memory().free) / float(psutil.virtual_memory().total)
print(u"物理内存： %s G" % total)
print(u"剩余物理内存： %s G" % free)
print(u"物理内存使用率： %s %%" % int(memory * 100))
# 系统启动时间
print(u"系统启动时间: %s" % datetime.datetime.fromtimestamp(psutil.boot_time()).strftime("%Y-%m-%d %H:%M:%S"))

users_count = len(psutil.users())

users_list = ",".join([u.name for u in psutil.users()])
print(u"当前有%s个用户，分别是 %s" % (users_count, users_list))
```

#### 4.3 硬盘使用率采集脚本

```python
#!/bin/python
#coding:utf-8

import psutil

disk = psutil.disk_partitions()
for i in disk:
    print "磁盘：%s   分区格式:%s"%(i.device,i.fstype)
    disk_use = psutil.disk_usage(i.mountpoint)
    print "使用了：%sM,空闲：%sM,总共：%sM,使用率\033[1;31;42m%s%%\033[0m,"%(disk_use.used/1024/1024,disk_use.free/1024/1024,disk_use.total/1024/1024,disk_use.percent)
```

#### 4.4 网络流量采集脚本

```python
#!/bin/python
#coding:utf-8

import psutil
import time

#网卡，可以得到网卡属性，连接数，当前流量等信息
net = psutil.net_io_counters()
bytes_sent = '{0:.2f} Mb'.format(net.bytes_recv / 1024 / 1024)
bytes_rcvd = '{0:.2f} Mb'.format(net.bytes_sent / 1024 / 1024)
print(u"网卡接收流量 %s 网卡发送流量 %s" % (bytes_rcvd, bytes_sent))
```



### 5. 系统批量运维管理

paramiko是用python语言写的一个模块，遵循SSH2协议，支持以加密和认证的方式，进行远程服务器的连接。



#### 5.1  用户名和密码连接脚本

##### 5.1.1 未封装脚本

```python
#!/bin/python
#coding:utf-8

import paramiko
   
# 创建SSH对象
ssh = paramiko.SSHClient()
# 允许连接不在know_hosts文件中的主机
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
# 连接服务器
ssh.connect(hostname='192.168.1.22', port=22, username='root', password='admin123')
# 执行命令
stdin, stdout, stderr = ssh.exec_command('ls')
# 获取命令结果
result = stdout.read()
   
# 关闭连接
ssh.close()
```



##### 5.1.2 SSHClient 封装 Transport脚本

```python
#!/bin/python
#coding:utf-8

import paramiko

transport = paramiko.Transport(('192.168.1.22', 22))
transport.connect(username='root', password='admin123')
ssh = paramiko.SSHClient()
ssh._transport = transport
stdin, stdout, stderr = ssh.exec_command('ifconfig')
print stdout.read()
transport.close()
```



#### 5.2 公钥和私钥连接脚本

##### 5.2.1 未封装脚本

```python
#!/bin/python
#coding:utf-8

import paramiko

private_key = paramiko.RSAKey.from_private_key_file('/home/auto/.ssh/id_rsa')  
# 创建SSH对象
ssh = paramiko.SSHClient()
# 允许连接不在know_hosts文件中的主机
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
# 连接服务器
ssh.connect(hostname='c1.salt.com', port=22, username='wupeiqi', key=private_key)
  
# 执行命令
stdin, stdout, stderr = ssh.exec_command('df')
# 获取命令结果
result = stdout.read()
  
# 关闭连接
ssh.close()
```

##### 5.2.2 SSHClient 封装 Transport脚本

```python
#!/bin/python
#coding:utf-8

import paramiko

private_key = paramiko.RSAKey.from_private_key_file('/root/.ssh/id_rsa')
transport = paramiko.Transport(('192.168.1.22', 22))
transport.connect(username='root', pkey=private_key)
ssh = paramiko.SSHClient()
ssh._transport = transport
stdin, stdout, stderr = ssh.exec_command('df')
print stdout.read()
transport.close()
```

#### 5.3 sftp上传和下载脚本

```python
#!/bin/python
import os,sys
import paramiko

t = paramiko.Transport(('192.168.1.22',22))
t.connect(username='root',password='admin123')
sftp = paramiko.SFTPClient.from_transport(t)
sftp.put('C:\Users\yunwei\Desktop\error.jpg','/home/yunwei/error.jpg')
#将error.jpg上传到服务器/home/yangmv目录
sftp.get('/home/yunwei/sftp.txt','C:\Users\yunwei\Desktop\sftp.txt')
#将sftp.txt下载到本机桌面
t.close()
```

#### 5.4 批量主机命令执行脚本

```python
#!/bin/python
#coding:utf-8

import paramiko
port=22
username="root"
file=open("ip.list")
for line in file:
    hostname=str(line.split("\t")[0])
    password=str(line.split("\t")[4]).strip()
    print "##########################",hostname,"########################"
    s=paramiko.SSHClient()
    s.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    s.connect(hostname,port,username,password)
    stdin,stdout,sterr=s.exec_command("df -Th")
    print stdout.read()
    s.close()
file.close()


# ip.list
test1   192.168.1.22    22      root    admin123
test2   192.168.1.23    22      root    Aa123456
```
