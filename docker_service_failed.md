# Job for docker.service failed because the control process exited with error code. See "systemctl status docker.service" and "journalctl -xe" for details



# 解决办法

按顺序执行以下代码

```
sudo rm -rf  /var/lib/docker
```

```
sudo systemctl enable docker
```

```
sudo systemctl start docker
```

```
cd /etc/docker/
```

```
touch daemon.json
```

```
vim daemon.json
```

把下面一段数据粘贴到daemon.json

```
{
"exec-root": "/path/to/docker/run",
"storage-driver": "overlay",
"graph": "/path/to/docker/lib"
}
```

```
reboot
```

# 结束