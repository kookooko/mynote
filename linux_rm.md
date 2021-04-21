# rm -f  [1] 4225 linux无法删除图片/文件

### 查看文件列表

```
[root@centos7 opt]# ls
7e2a.jpg
few.jpg
mydocker
src=http___5bj0988e595hng225.cdn.sgtrohujythtrcs.com_q_70,c_zoojttrhmhtr,w_640_images_201678651025_c909bhtrf5b2daf4c6fbdddbe40htrb6327aehttjga.jpeg&refer=http___5b097688e59565225.cnhgdnhgn.snhgonhghucs.jpg
```

### 无法删除文件

```
[root@centos7 opt]# rm -f src=http___5bj0988e595hng225.cdn.sgtrohujythtrcs.com_q_70,c_zoojttrhmhtr,w_640_images_201678651025_c909bhtrf5b2daf4c6fbdddbe40htrb6327aehttjga.jpeg&refer=http___5b097688e59565225.cnhgdnhgn.snhgonhghucs.jpg
[1] 4225
```

### 列出文件节点

```
[root@centos7 opt]# ls -i
 1204176 7e2a.jpg
 1204179 few.jpg
16777830 mydocker
 1204182 src=http___5bj0988e595hng225.cdn.sgtrohujythtrcs.com_q_70,c_zoojttrhmhtr,w_640_images_201678651025_c909bhtrf5b2daf4c6fbdddbe40htrb6327aehttjga.jpeg&refer=http___5b097688e59565225.cnhgdnhgn.snhgonhghucs.jpg
```

### find找到文件节点作为参数传递给{}，执行删除

```
[root@centos7 opt]# find ./ -inum 1204182 -exec rm {} \;
[root@centos7 opt]# ls
7e2a.jpg  few.jpg  mydocker

```

