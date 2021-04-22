### 虚拟机修改静态ip之后

### WARNING: IPv4 forwarding is disabled. Networking will not work.

```
[root@centos7 /]# docker run -p 3306:3306 --name mysql \
> -v /usr/local/docker/mysql/conf:/etc/mysql \
> -v /usr/local/docker/mysql/logs:/var/log/mysql \
> -v /usr/local/docker/mysql/data:/var/lib/mysql \
> -e MYSQL_ROOT_PASSWORD=root \
> -d mysql:5.7
WARNING: IPv4 forwarding is disabled. Networking will not work.
```

- #### 修改配置文件：

```
vim /usr/lib/sysctl.d/00-system.conf
```

- #### 添加

```
net.ipv4.ip_forward=1
```

- #### 重启虚拟机网络

```
[root@centos7 /]# systemctl restart network
```

- #### 再试一下，好了

```
[root@centos7 /]# docker run -p 3306:3306 --name mysql \
> -v /usr/local/docker/mysql/conf:/etc/mysql \
> -v /usr/local/docker/mysql/logs:/var/log/mysql \
> -v /usr/local/docker/mysql/data:/var/lib/mysql \
> -e MYSQL_ROOT_PASSWORD=root \
> -d mysql:5.7
382e7b268691face19ede79e936e476cbbd5a8b9c6dd2b3deb4cb9ad734af0dc
```

