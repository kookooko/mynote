先执行

```
mkdir -p /usr/local/docker/nacos/init.d/custom.properties
```

```
version: "2"
services:
  nacos:
    image: nacos/nacos-server:latest
    container_name: nacos
    env_file:
      - ./nacos-standlone-mysql.env
    volumes:
      - /usr/local/docker/nacos/standalone-logs:/home/nacos/logs
      - /usr/local/docker/nacos/init.d/custom.properties:/home/nacos/init.d/custom.properties
    ports:
      - "8848:8848"
      - "9848:9848"
      - "9555:9555"
    depends_on:
      - mysql
    restart: always
  mysql:
    container_name: mysql
    image: mysql:5.7
    env_file:
      - ./mysql.env
    volumes:
      - /usr/local/docker/mysql/conf:/etc/mysql
      - /usr/local/docker/mysql/logs:/var/log/mysql
      - /usr/local/docker/mysql/data:/var/lib/mysql
    restart: always
    ports:
      - "3306:3306"
```

nacos-standlone-mysql.env

```
PREFER_HOST_MODE=hostname
MODE=standalone
SPRING_DATASOURCE_PLATFORM=mysql
MYSQL_SERVICE_HOST=mysql
MYSQL_SERVICE_PORT=3306
MYSQL_SERVICE_USER=root
MYSQL_SERVICE_PASSWORD=root
```

mysql.env

```
MYSQL_ROOT_PASSWORD=root
```

