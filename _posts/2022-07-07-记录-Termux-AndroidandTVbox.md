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

```bash
pkg install cmatrix
```

Run

```bash
cmatrix
```

火车特效

```bash
pkg install sl
```

Run

```bash
sl
```

### 扫描网络

如果要在不同去查看局域网的情况下知道电视的ip地址，那么就需要对局域网进行扫描，我们可以使用`nmap`来完成这个事情。

在termux中安装nmap

`pkg install nmap`

扫描ip是否up

`nmap -sn iprange`

因为安卓手机没有被root，所以好像用pingscan没办法扫出存活的ip，第二就算知道这个ip也必须用problescan才能扫出开放的端口

`nmap -Pn ip`   






















