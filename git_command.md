## 记录我的git初始化流程

### 我的文件目录/mynote

````
/mynote
$ git init
Initialized empty Git repository in E:/mynote/.git/

/mynote (master)
$ git config --list
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=openssl
http.sslcainfo=D:/Git/mingw64/ssl/certs/ca-bundle.crt
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
credential.helper=manager-core
credential.https://dev.azure.com.usehttppath=true
init.defaultbranch=master
user.name=myusername
user.email=myemail@xxx.com
push.default=simple
core.repositoryformatversion=0
core.filemode=false
core.bare=false
core.logallrefupdates=true
core.symlinks=false
core.ignorecase=true


/mynote (master)
$ git config --global user.name "root"

/mynote (master)
$ git config --global user.email "root@root.com"

/mynote (master)
$ git config --global --list
user.name=root
user.email=root@root.com
push.default=simple

/mynote (master)
$ git config --global credential.helper wincred

/mynote (master)
$ git config --global --list
user.name=root
user.email=root@root.com
push.default=simple
credential.helper=wincred
````

- #### 直接使用 git config --global "user.change@change.com" 修改不行，这是我蒙的，以为能修改

```
/mynote (master)
$ git config --global "user.change@change.com"

/mynote (master)
$ git config --global --list
user.name=root
user.email=root@root.com
push.default=simple
credential.helper=wincred
```

- #### 使用git config --global --replace-all user.name "myemail@xxx.com"修改

```


/mynote (master)
$ git config --global --replace-all user.name "myemail@xxx.com"

/mynote (master)
$ git config --global --list
user.name=myemail@xxx.com
user.email=root@root.com
push.default=simple
credential.helper=wincred

/mynote (master)
$ git config --global --replace-all user.email "myemail@xxx.com"

/mynote (master)
$ git config --global --list
user.name=myemail@xxx.com
user.email=myemail@xxx.com
push.default=simple
credential.helper=wincred

/mynote (master)
$ git config --global --replace-all user.name "myusername"

/mynote (master)
$ git config --global --list
user.name=myusername
user.email=myemail@xxx.com
push.default=simple
credential.helper=wincred

/mynote (master)
$ git-keygen -t rsa -C "myemail@xxx.com"
bash: git-keygen: command not found

/mynote (master)
$ ssh-keygen -t rsa -C "myemail@xxx.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/myname/.ssh/id_rsa):
/c/Users/myname/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/myname/.ssh/id_rsa
Your public key has been saved in /c/Users/myname/.ssh/id_rsa.pub
The key fingerprint is:
xxx

/mynote (master)
$ cat id_rsa.pub
cat: id_rsa.pub: No such file or directory

/mynote (master)
$ cat /c/Users/myname/.ssh/id_rsa.pub
```



### git 查看配置

```

$ git config --global --list
user.name=myusername
user.email=myemail@xxx.com
push.default=simple
credential.helper=wincred
```

