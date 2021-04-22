```
docker search nacos

Error response from daemon: Get https://index.docker.io/v1/search?q=nacos
```

通过谷歌的114.114.114.114  DNS服务器获得正确的ip

```
dig @114.114.114.114 index.docker.io

-bash: dig: command not found
```



```
yum -y install bind-utils
```



