---
published: true
categories: 技术
---
## 通过Termux在同一个wifi中启动电视的adb安装TVbox

之前每次想要给智能电视安装软件都需要自己带一台电脑，这种方式非常的不方便，于是想到了通过手机安装一个**Termux**模拟器的方式来让自己能够随时地安装软件。

首先手机下载Termux.apk, 下载链接[Termux](https://f-droid.org/repo/com.termux_117.apk),然后安装该软件。

使用之前输入下面的命令初始化：

```bash
apt update 

%更新源

apt upgrade

%更新软件和依赖
```

### Some interesting package

黑客特效


`pkg install cmatrix`

Run

`cmatrix`

火车特效

`pkg install sl`

Run

`sl`

### 扫描网络

如果要在不同去查看局域网的情况下知道电视的ip地址，那么就需要对局域网进行扫描，我们可以使用`nmap`来完成这个事情。

在termux中安装nmap

`pkg install nmap`

扫描ip是否up

`nmap -sn iprange`

因为安卓手机没有被root，所以好像用pingscan没办法扫出存活的ip，第二就算知道这个ip也必须用problescan才能扫出开放的端口

`nmap -Pn ip`   

因为使用原生的ping是没有问题的，所以就写了一段python的pingscan扫描存活的ip,这儿是使用135端口，windows默认开启135端口

```python

import socket
from datetime import datetime
net = input("Enter the IP address: ")
net1 = net.split('.')
a = '.'

net2 = net1[0] + a + net1[1] + a + net1[2] + a
st1 = int(input("Enter the Starting Number: "))
en1 = int(input("Enter the Last Number: "))
en1 = en1 + 1
t1 = datetime.now()

def scan(addr):
   s = socket.socket(socket.AF_INET,socket.SOCK_STREAM)
   socket.setdefaulttimeout(1)
   result = s.connect_ex((addr,135))
   if result == 0:
      return 1
   else :
      return 0

def run1():
   for ip in range(st1,en1):
      addr = net2 + str(ip)
      if (scan(addr)):
         print (addr , "is live")
         
run1()
t2 = datetime.now()
total = t2 - t1
print ("Scanning completed in: " , total)

```

通用的ping sweep扫描

```python

import os
import platform

from datetime import datetime
net = input("Enter the Network Address: ")
net1= net.split('.')
a = '.'

net2 = net1[0] + a + net1[1] + a + net1[2] + a
st1 = int(input("Enter the Starting Number: "))
en1 = int(input("Enter the Last Number: "))
en1 = en1 + 1
oper = platform.system()

if (oper == "Windows"):
   ping1 = "ping -n 1 "
elif (oper == "Linux"):
   ping1 = "ping -c 1 "
else :
   ping1 = "ping -c 1 "
t1 = datetime.now()
print ("Scanning in Progress:")

for ip in range(st1,en1):
   addr = net2 + str(ip)
   comm = ping1 + addr
   response = os.popen(comm)
   
   for line in response.readlines():
      if(line.count("TTL")):
         break
      if (line.count("TTL")):
         print (addr, "--> Live")
         
t2 = datetime.now()
total = t2 - t1
print ("Scanning completed in: ",total)

```

### 安装adb，使用adb安装tvbox

adb已经集成到`termux-platform-tools`里面了，所以安装adb，只需要安装这个包

`pkg install platform-tools`


下载tvbox到终端中，使用curl命令

`curl -s http://y8lc.692657.com/com.github.tvbox.osc.apk -o tvbox.apk`

然后通过上面的pingscan发现电视ip，电视打开调试过后，adb连接这个ip

`adb connect ip`

最后是安装这个软件

`adb install tvbox.apk`

最后就是愉快地使用吧！！！






















