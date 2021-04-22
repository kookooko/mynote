修改ifcfg-eth0（名字可能不一样）

```
vi /etc/sysconfig/network-scripts/ifcfg-eth0
```

ifcfg-eth0内容

```
TYPE="Ethernet"
PROXY_METHOD="none"
BROWSER_ONLY="no"
BOOTPROTO="static"
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
IPADDR="192.168.3.119"
NETMASK="255.255.255.0"
GATWAY="192.168.3.1"
DNS1="114.114.114.114"
```

