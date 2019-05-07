Centos7设置静态IP

-查询网卡名称

```shell
ip addr
```

显示如下

```shell
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:ca:0d:e8 brd ff:ff:ff:ff:ff:ff
    inet 192.168.20.131/24 brd 192.168.20.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::9509:6916:df2e:2521/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```

其中第1个“lo” 是本地回环的信息；第2个“enp0s3”是我们要修改是我们要配置的网卡。

编辑/etc/sysconfig/network-scripts/目录下的配置文件“ifcfg-enp0s3”

将 BOOTPROTO=“dhcp” 改为 BOOTPROTO=“static”

然后增加配置

IPADDR=固定ip地址 

NETMASK=子网掩码

GATEWAY=网关



重启网络服务

service network restart

增接dns配置

编辑文件/etc/resolv.conf

增加配置

nameserver 网关

nameserver 114.114.114.114

nameserver 8.8.8.8

