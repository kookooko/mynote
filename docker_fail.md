### Error response from daemon: OCI runtime create failed: container with id exists: 

```
[root@centos7 ~]# docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED        STATUS                       PORTS                                                  NAMES
c969b8bdf507   redis          "docker-entrypoint.s…"   7 hours ago    Exited (255) 5 minutes ago   0.0.0.0:6379->6379/tcp, :::6379->6379/tcp              redis
89a284777f5a   mysql:5.7      "docker-entrypoint.s…"   8 hours ago    Exited (255) 5 minutes ago   0.0.0.0:3306->3306/tcp, :::3306->3306/tcp, 33060/tcp   mysql
91034e80a65f   d1165f221234   "/hello"                 13 hours ago   Exited (0) 13 hours ago                                                             nostalgic_solomon
```

```
[root@centos7 ~]# docker start 89a284777f5a
Error response from daemon: OCI runtime create failed: container with id exists: 89a284777f5a65f9606a3158f0794913c73285a20d83b22cd1564633f4ac0a6f: unknown
Error: failed to start containers: 89a284777f5a
```

```
[root@centos7 ~]# find / -name 89a284777f5a65f9606a3158f0794913c73285a20d83b22cd1564633f4ac0a6f
/path/to/docker/lib/containers/89a284777f5a65f9606a3158f0794913c73285a20d83b22cd1564633f4ac0a6f
/path/to/docker/lib/image/overlay/layerdb/mounts/89a284777f5a65f9606a3158f0794913c73285a20d83b22cd1564633f4ac0a6f
/path/to/docker/run/runtime-runc/moby/89a284777f5a65f9606a3158f0794913c73285a20d83b22cd1564633f4ac0a6f
```

```
[root@centos7 ~]# rm -rf /path/to/docker/run/runtime-runc/moby/89a284777f5a65f9606a3158f0794913c73285a20d83b22cd1564633f4ac0a6f/
```

```
[root@centos7 ~]# docker start 89a284777f5a
89a284777f5a
```

