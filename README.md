### ARM机可用
自用魔改一键DD脚本，仅支持密钥登录，SSH端口22345<br>
```
bash <(curl -k https://raw.githubusercontent.com/daoke123/SHELL/master/NetReinstallDebian.sh) 

默认为Debian11，下参数可手动调整
--version 10
默认64位系统，下参数可指定为ARM
--architecture arm64
默认为Debian的CDN源，下参数可指定为清华源，加快下载速度
--china
指定apt源地址
--mirror-host ftp.hk.debian.org

指定网卡，貌似尚不支持，建议在 preed.cfg 里手动添加 d-i netcfg/choose_interface select ens4
```

### Linux 网络重装系统脚本
自用魔改一键DD脚本，仅支持密钥登录，SSH端口22345<br>
```
bash <(curl -k https://raw.githubusercontent.com/GouGoGoal/SHELL/master/InstallNET.sh) -d 10 -v 64 -a [-p PassWord] [-i eth0] [--mirror  ...]
```
-d 10 为Debian 10<br>
-v 为64位系统<br>
-a 自动运行，无需在VNC里手动操作(理想情况下)<br>
-i 指定网卡，多网卡的时候需要指定，单网卡可以忽略<br>
--mirror 指定源，同地区的源装系统会更快，默认是美国源，下方为Debian源<br>
```
大陆源
--mirror 'http://mirrors.ustc.edu.cn/debian/'
香港源
--mirror 'http://ftp.hk.debian.org/debian/'
台湾源
--mirror 'http://ftp.tw.debian.org/debian/'
日本源
--mirror 'http://ftp.jp.debian.org/debian/'
韩国
--mirror 'http://ftp.kr.debian.org/debian/'
新加坡
--mirror 'http://mirror.0x.sg/debian/'
俄罗斯
--mirror 'http://ftp.ru.debian.org/debian/'
```
### [forward.sh](https://raw.githubusercontent.com/GouGoGoal/SHELL/master/forward.sh) iptables端口转发工具
使用iptables进行转发，性能最快，但不支持负载均衡，下载完成后编辑查看如何使用<br>
### [常用iptables命令](iptables.md)  

### 一键添加swap
```
bash <(curl -k https://raw.githubusercontent.com/GouGoGoal/SHELL/master/addswap.sh) [1024]
```
某些模板开机的Linux系统没有swap，添加swap以提高系统稳定性<br>
参数以M为单位添加，若没有参数则添加和当前RAM一样大小的swap<br>
### [BestTrace](https://raw.githubusercontent.com/GouGoGoal/SHELL/master/besttrace) 路由追踪工具
下载到Linux上，给执行权限，就可以了，besttrace [-g cn] 1.1.1.1<br>
### 一键测试回程路由
```
bash <(curl -k https://raw.githubusercontent.com/GouGoGoal/SHELL/master/mtr.sh)
```
### [TCPing](https://raw.githubusercontent.com/GouGoGoal/SHELL/master/tcping) 查看TCP延迟
下载到Linux上，给执行权限，就可以了，tcping 1.1.1.1<br>
### [SpeedTest](https://raw.githubusercontent.com/GouGoGoal/SHELL/master/speedtest) 没啥好说的，给执行权限就行了
### [Nginx](https://github.com/GouGoGoal/SHELL/tree/master/Nginx) 的使用方法技巧
### [PHP](https://github.com/GouGoGoal/SHELL/tree/master/PHP) 的apt安装以及部分优化
### [Mysql](https://github.com/GouGoGoal/SHELL/tree/master/Mysql) 的apt安装以及部分优化
### [CC脚本](https://github.com/GouGoGoal/SHELL/raw/master/cc.py) 
```
#升级最新版内核
echo "deb `cat /etc/apt/sources.list|grep deb-src|awk '{print $2,$3}'`-backports main" >> /etc/apt/sources.list
apt update
apt -t `cat /etc/apt/sources.list|grep deb-src|awk '{print $3}'`-backports install linux-image-$(dpkg --print-architecture) linux-headers-$(dpkg --print-architecture) -y 

update-grub


#调整内核启动顺序
cat /boot/grub/grub.cfg |grep "menuentry "

vi /etc/default/grub
GRUB_DEFAULT=0 修改为Advanced options for Debian GNU/Linux>内核名字 ("Advanced options for Debian GNU/Linux>Debian GNU/Linux, with Linux 5.10.0-0.bpo.8-amd64")
update-grub
```

```
#免密登录，公钥换成自己的
mkdir /root/.ssh;echo "ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA5qK3fDbxZshKP3MbQo4xm1YNmTQsHcapbF8wAXJJcCgxtzujH9QuFCeQzsQ3QET2qZgG1k0GfTV6slRdrJJeI8fdwFgRc28JEhXh4rGx8MUdotJh8eVAnygWATBtet2Au5gpn3s3s44XqgnWXY+bRGJ6WoB58/3fjPG1YZIR5wh9knNxRt/9VO8YCTBqQP3z5hdPuNldx3jgIuFNhcI1qBVnQZ2czC2Zv8sHDDuiuNoaomKsg7LgbhKPnvRfEGb+yZaU/KKwbEJwbFcZkT7QiW90OhYVKT2+K8xEsUpR4ocH+SxgvFrpyKAXkSqF/Wwe32baAlzrNwucLdsS+jBk3w== OpenSSH-rsa-import-061520" >>/root/.ssh/authorized_keys

```


