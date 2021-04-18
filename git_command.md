````

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote
$ git init
Initialized empty Git repository in E:/mynote/.git/

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
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
user.name=kookooko
user.email=loyojo888@outlook.com
push.default=simple
core.repositoryformatversion=0
core.filemode=false
core.bare=false
core.logallrefupdates=true
core.symlinks=false
core.ignorecase=true


Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ git config --global user.name "root"

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ git config --global user.email "root@root.com"

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ git config --global --list
user.name=root
user.email=root@root.com
push.default=simple

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ git config --global credential.helper wincred

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ git config --global --list
user.name=root
user.email=root@root.com
push.default=simple
credential.helper=wincred

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ git config --global "user.wsgdcwfhtwr@outlook.com"

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ git config --global --list
user.name=root
user.email=root@root.com
push.default=simple
credential.helper=wincred

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ git config --global --replace-all user.name "wsgdcwfhtwr@outlook.com"

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ git config --global --list
user.name=wsgdcwfhtwr@outlook.com
user.email=root@root.com
push.default=simple
credential.helper=wincred

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ git config --global --replace-all user.email "wsgdcwfhtwr@outlook.com"

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ git config --global --list
user.name=wsgdcwfhtwr@outlook.com
user.email=wsgdcwfhtwr@outlook.com
push.default=simple
credential.helper=wincred

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ git config --global --replace-all user.name "kookooko"

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ git config --global --list
user.name=kookooko
user.email=wsgdcwfhtwr@outlook.com
push.default=simple
credential.helper=wincred

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ git-keygen -t rsa -C "wsgdcwfhtwr@outlook.com"
bash: git-keygen: command not found

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ ssh-keygen -t rsa -C "wsgdcwfhtwr@outlook.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/Lenovo_L/.ssh/id_rsa):
/c/Users/Lenovo_L/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/Lenovo_L/.ssh/id_rsa
Your public key has been saved in /c/Users/Lenovo_L/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:l3oX4VcuCLW59PUJjbDN8GdK2uvObX7WjH+8Tw4AUEU wsgdcwfhtwr@outlook.com
The key's randomart image is:
+---[RSA 3072]----+
|        ...=E    |
|         . .Boo  |
|          o.=B +o|
|           *+==+o|
|        S o.*o+.o|
|         o   +.. |
|        . . ...+o|
|         . .o o=B|
|            .+o*O|
+----[SHA256]-----+

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ cat id_rsa.pub
cat: id_rsa.pub: No such file or directory

Lenovo_L@LAPTOP-4Q0GEQ74 MINGW64 /e/mynote (master)
$ cat /c/Users/Lenovo_L/.ssh/id_rsa.pub

````

```
git 查看配置

$ git config --global --list
user.name=kookooko
user.email=wsgdcwfhtwr@outlook.com
push.default=simple
credential.helper=wincred
```

