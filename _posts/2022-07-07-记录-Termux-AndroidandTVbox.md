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
