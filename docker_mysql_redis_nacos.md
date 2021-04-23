# docker部署mysql redis nacos

## docker启动mysql容器流程

```
docker pull mysql:5.7
```

```
docker run -p 3306:3306 --name mysql \
-v /usr/local/docker/mysql/conf:/etc/mysql \
-v /usr/local/docker/mysql/logs:/var/log/mysql \
-v /usr/local/docker/mysql/data:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=root \
-d mysql:5.7
```

- ### 配置mysql

```
vim /usr/local/docker/mysql/conf/my.cnf
```

- ### my.cnf内容

```
[mysqld]
character-set-server=utf8
collation-server=utf8_unicode_ci
skip-name-resolve

[client]
default-character-set=utf8

[mysql]
default-character-set=utf8
```

- #### 设置mysql容器自启动

```
[root@centos7 conf]# docker update mysql --restart=always
mysql
```



## docker启动redis容器流程

```
docker pull redis
```

```
mkdir -p /usr/local/docker/redis/conf
```

```
touch /usr/local/docker/redis/conf/redis.conf
```

- ### redis.conf内容如下

```
appendonly yes
```

- ### redis-server /etc/redis/redis.conf

- ### 容器中reids每次以/etc/redis/redis.conf配置文件启动

```
docker run -p 6379:6379 --name redis \
-v /usr/local/docker/redis/data:/data \
-v /usr/local/docker/redis/conf/redis.conf:/etc/redis/redis.conf \
-d redis redis-server /etc/redis/redis.conf
```

- ### docker exec -it redis redis-cli

- ### redis-cli直接链接redis

```
[root@centos7 /]# docker exec -it redis redis-cli
127.0.0.1:6379> set a b
OK
127.0.0.1:6379> get a
"b"
127.0.0.1:6379> 

```

- #### reids默认数据存在内存，非持久化，修改redis.conf使redis持久化

```
vim /mydata/redis/conf/redis.conf
```

- #### redis.conf添加内容

```
appendonly yes
```

```
docker restart redis
```

- #### 设置redis自启动

```
[root@centos7 /]# docker update redis --restart=always
redis
```

# nacos

- #### 拉取镜像

```undefined
docker pull nacos/nacos-server
```

- #### 挂载目录

```bash
mkdir -p /usr/local/docker/nacos/logs/
mkdir -p /usr/local/docker/nacos/init.d/
vim /usr/local/docker/nacos/init.d/custom.properties
```

- #### custom.properties内容

```cpp
server.contextPath=/nacos
server.servlet.contextPath=/nacos
server.port=8848

spring.datasource.platform=mysql

db.num=1
db.url.0=jdbc:mysql://localhost:3306/nacos?characterEncoding=utf8&connectTimeout=1000&socketTimeout=3000&autoReconnect=true
db.user=root
db.password=root


nacos.cmdb.dumpTaskInterval=3600
nacos.cmdb.eventTaskInterval=10
nacos.cmdb.labelTaskInterval=300
nacos.cmdb.loadDataAtStart=false

management.metrics.export.elastic.enabled=false

management.metrics.export.influx.enabled=false


server.tomcat.accesslog.enabled=true
server.tomcat.accesslog.pattern=%h %l %u %t "%r" %s %b %D %{User-Agent}i


nacos.security.ignore.urls=/,/**/*.css,/**/*.js,/**/*.html,/**/*.map,/**/*.svg,/**/*.png,/**/*.ico,/console-fe/public/**,/v1/auth/login,/v1/console/health/**,/v1/cs/**,/v1/ns/**,/v1/cmdb/**,/actuator/**,/v1/console/server/**
nacos.naming.distro.taskDispatchThreadCount=1
nacos.naming.distro.taskDispatchPeriod=200
nacos.naming.distro.batchSyncKeyCount=1000
nacos.naming.distro.initDataRatio=0.9
nacos.naming.distro.syncRetryDelay=5000
nacos.naming.data.warmup=true
nacos.naming.expireInstance=true
```

- #### 启动容器

```
docker  run \
--name nacos -d \
-p 8848:8848 \
--privileged=true \
--restart=always \
-e JVM_XMS=256m \
-e JVM_XMX=256m \
-e MODE=standalone \
-e PREFER_HOST_MODE=hostname \
-v /usr/local/docker/nacos/logs:/home/nacos/logs \
-v /usr/local/docker/nacos/init.d/custom.properties:/home/nacos/init.d/custom.properties \
nacos/nacos-server
```

- #### 设置nacos容器自启动

```
docker update nacos --restart=always
```

