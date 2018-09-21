# 断网限制

绕过校园网验证，需要保证校内DNS服务器是在断网后有开放的。可以先通过切断校园网，后在终端ping github.com来验证是否可以正常获得IP地址。

## 安装 SoftEther VPN Server

1.下载编译工具

```
yum  install build-essential
yum install wget
```

2.下载VPN
```
#32位系统
wget http://oks2t4o68.bkt.clouddn.com/softether-vpnserver-v4.22-9634-beta-2016.11.27-linux-x86-32bit.tar.gz
#64位系统
wget http://oks2t4o68.bkt.clouddn.com/softether-vpnserver-v4.22-9634-beta-2016.11.27-linux-x64-64bit.tar.gz
```
3.解压并编译
```
#解压缩
tar xvf 文件名
#进入目录
cd vpnserver
#编译
make
```
4.安装

3个选项都选"1. Yes"

![](https://i.imgur.com/3TDOnR6.png)

5.配置服务
```
#开启服务
./vpnserver start
#设置
./vpncmd
```
![](https://i.imgur.com/kl4yocL.png)

依次1，回车，回车，进入如下操作

![](https://i.imgur.com/4tZF2TE.png)

输入ServerPasswordSet后来设置密码

## 云服务器防火墙

如果服务器有开启防火墙，需要放行443,53端口。一般云主机都自带一个防火墙规则，需要配置相应端口。

> 以下为阿里云配置

1.进入安全组

![](https://i.imgur.com/N9AULMQ.png)

2.创建安全组

![](https://i.imgur.com/juQ5rFs.png)

![](https://i.imgur.com/xsm4Uzd.png)

3.配置安全组

![](https://i.imgur.com/VX12Pw6.png)

4.添加规则

可以设置放行所有端口，出方向也同理
![](https://i.imgur.com/XoWfXKL.png)

![](https://i.imgur.com/R0bnliI.png)

## 安装本地 SoftEther VPN Server 管理工具

1.安装

打开名如softether-vpnserver_vpnbridge.exe的文件，选择如下

![](https://i.imgur.com/osruTmK.png)

2.配置

打开管理工具，点击新设置，设置内容如下。

![](https://i.imgur.com/RzSJ2yC.png)

3.设置加密网络

![](https://i.imgur.com/AAb40Va.png)

点击加密与网络，VPN over ICMP / DNS 设置，勾选53号端口，确定。

4.管理用户

点击管理虚拟HUB，管理用户，新建，输入用户名和密码，确定。

5.开启DHCP服务

点击虚拟NAT和虚拟DHCP服务器，启动SecureNAT。

![](https://i.imgur.com/uJhMIst.png)

## 安装本地 SoftEther VPN Client

1.安装
打开名如softether-vpnclient.exe，选择如下，然后安装

![](https://i.imgur.com/JZ181rd.png)

2.设置

打开client软件，安装虚拟网卡

![](https://i.imgur.com/CiFZzIm.png)

3.添加连接

点击添加新的VPN连接，配置如下内容。

![](https://i.imgur.com/UtbiX6G.png)

> 连接成功后会显示分配的内网IP，之后关闭校园网，再次连接，应该也是没问题的。
