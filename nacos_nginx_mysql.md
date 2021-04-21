```yaml
# docker-compose参考：https://github.com/nacos-group/nacos-docker/blob/master/example/standalone-mysql-5.7.yaml
version: '3'
services:
  nacos:
    image: nacos/nacos-server:latest                             # 镜像`nacos/nacos-server:latest`
    container_name: mynacos                                 # 容器名为'mynacos'
    restart: always                                              # 指定容器退出后的重启策略为始终重启
    volumes:                                                     # 数据卷挂载路径设置,将本机目录映射到容器目录
      - "./nacos_mysql/logs:/home/nacos/logs"
      - "./nacos_mysql/init.d/custom.properties:/home/nacos/init.d/custom.properties"
      - "./nacos_mysql/conf/application.properties:/home/nacos/conf/application.properties"
    environment:                        # 设置环境变量,相当于docker run命令中的-e
      - PREFER_HOST_MODE=hostname                 # 如果支持主机名可以使用hostname,否则使用ip，默认也是ip
      - MODE=standalone                           # 单机模式启动
      - SPRING_DATASOURCE_PLATFORM=mysql          # 数据源平台 仅支持mysql或不保存empty
      - MYSQL_SERVICE_HOST=192.168.3.119    # 注：这里不能为`127.0.0.1`或`localhost`方式！！！
      - MYSQL_SERVICE_DB_NAME=nacos_sql        # 所需sql脚本位于 `nacos-mysql/nacos-mysql.sql`
      - MYSQL_SERVICE_PORT=3306
      - MYSQL_SERVICE_USER=root
      - MYSQL_SERVICE_PASSWORD=root
      # JVM调优参数
      - JVM_XMS=64m   #-Xms default :2g
      - JVM_XMX=64m   #-Xmx default :2g
      - JVM_XMN=16m   #-Xmn default :1g
      - JVM_MS=8m     #-XX:MetaspaceSize default :128m
      - JVM_MMS=8m    #-XX:MaxMetaspaceSize default :320m
      - NACOS_DEBUG=n #是否开启远程debug，y/n，默认n
      - TOMCAT_ACCESSLOG_ENABLED=false #是否开始tomcat访问日志的记录，默认false
    ports:                              # 映射端口
      - "8848:8848"
      - "9555:9555"
    mem_limit: 300m   # 最大使用内存
  nginx:
    image: nginx:latest                 # 镜像`nginx:latest`
    container_name: nginx               # 容器名为'nginx'
    restart: always                     # 指定容器退出后的重启策略为始终重启
    volumes:                            # 数据卷挂载路径设置,将本机目录映射到容器目录
      - "./nginx/conf/nginx.conf:/etc/nginx/nginx.conf"
      - "./nginx/conf/conf.d/default.conf:/etc/nginx/conf.d/default.conf"
      - "./nginx/html:/usr/share/nginx/html"
      - "./nginx/log:/var/log/nginx"
    environment:                        # 设置环境变量,相当于docker run命令中的-e
      TZ: Asia/Shanghai
      LANG: en_US.UTF-8
    ports:                              # 映射端口
      - "80:80"
```

