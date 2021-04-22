## linux虚拟机和主机能相互ping通，linux却不能访问外网

### 下面是试错过程

- #### 修改ifcfg-eth0（名字可能不一样）

```
vi /etc/sysconfig/network-scripts/ifcfg-eth0
```

- #### ifcfg-eth0内容，参考电脑网络设置

```
TYPE="Ethernet"
PROXY_METHOD="none"
BROWSER_ONLY="no"
BOOTPROTO="static"      #我是用的静态ip
DEFROUTE="yes"
IPV4_FAILURE_FATAL="no"
IPV6INIT="yes"
IPV6_AUTOCONF="yes"
IPV6_DEFROUTE="yes"
IPV6_FAILURE_FATAL="no"
IPV6_ADDR_GEN_MODE="stable-privacy"
NAME="ens33"
UUID="b688fdef-12fa-4157-9577-9c5ce06e74ee"
DEVICE="ens33"
ONBOOT="yes"
IPADDR="192.168.3.119"  #linux虚拟机地址
NETMASK="255.255.255.0" #子网掩码和电脑一样
GATWAY="192.168.3.1"    #网关和电脑一样
DNS1="114.114.114.114"  #域名和电脑一样
```

- #### 查看电脑网络设置

![image-20210422200735376](../Desktop/image-20210422200735376.png)

![image-20210422200803177](../Desktop/image-20210422200803177.png)

![image-20210422201011458](../Desktop/image-20210422201011458.png)

- #### 重启网络配置 

```
service network restart 
```



- #### ping一下百度试试,呵呵🙂

```
[root@centos7 init.d]# ping www.baidu.com
connect: Network is unreachable
```

- ### 使用route命令

- ### 下面的192.168.3.1（填自己的网关）

```
route add default gw 192.168.3.1
```

- #### 再ping一下百度试试,？？？😊

```
[root@centos7 network-scripts]# ping www.baidu.com
PING www.a.shifen.com (180.101.49.12) 56(84) bytes of data.
64 bytes from 180.101.49.12 (180.101.49.12): icmp_seq=1 ttl=53 time=14.1 ms
64 bytes from 180.101.49.12 (180.101.49.12): icmp_seq=2 ttl=53 time=12.6 ms
64 bytes from 180.101.49.12 (180.101.49.12): icmp_seq=3 ttl=53 time=17.1 ms
64 bytes from 180.101.49.12 (180.101.49.12): icmp_seq=4 ttl=53 time=13.7 ms
```

- #### 我还是不明白为什么前面设置了网关不管用

- #### 后来又反弹了，呵呵🙂，我只能先用上面的route命令撑一下

```
[root@centos7 init.d]# ping www.baidu.com
connect: Network is unreachable
```

