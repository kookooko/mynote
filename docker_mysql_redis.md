# docker部署mysql redis

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

