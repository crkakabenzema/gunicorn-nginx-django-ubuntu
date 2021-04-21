1. 安装数据库驱动：

pip install pymysql

2. pyton manage.py makemigrations:

   如果使用以上命令报了错
   “ RuntimeError: ‘cryptography’ package is required for sha256_password or caching_sha2_password auth m”

解决方法:使用这条命令:pip install cryptography安装成功就行



# 卸载 nginx 彻底删除

#### 卸载 删除 nginx

##### 1.删除nginx，–purge包括配置文件

```
sudo apt-get --purge remove nginx
1
```

##### 2.自动移除全部不使用的软件包

```
sudo apt-get autoremove
1
```

##### 3.罗列出与nginx相关的软件

```
dpkg --get-selections|grep nginx
1
```

执行结果:

```
stephen@stephen-OptiPlex-390:~$ dpkg --get-selections|grep nginx

nginx                       install
nginx-common                install
nginx-core                  install
12345
```

##### 4.删除3.查询出与nginx有关的软件

```
sudo apt-get --purge remove nginx
sudo apt-get --purge remove nginx-common
sudo apt-get --purge remove nginx-core
123
```

这样就可以完全卸载掉nginx包括配置文件

------

##### 5.查看nginx正在运行的进程，如果有就kill掉

```
ps -ef |grep nginx
1
```

看下nginx还有没有启动,一般执行完1后，nginx还是启动着的，如下：

```
stephen@stephen-OptiPlex-390:~$ ps -ef |grep nginx
root      7875  2317  0 15:02 ?        00:00:00 nginx: master process /usr/sbin/nginx
www-data  7876  7875  0 15:02 ?        00:00:00 nginx: worker process
www-data  7877  7875  0 15:02 ?        00:00:00 nginx: worker process
www-data  7878  7875  0 15:02 ?        00:00:00 nginx: worker process
www-data  7879  7875  0 15:02 ?        00:00:00 nginx: worker process
stephen   8321  3510  0 15:20 pts/0    00:00:00 grep --color=auto nginx
1234567
```

##### 6.kill nginx进程

```
sudo kill  -9  7875 7876 7877 7879
1
```

##### 7.全局查找与nginx相关的文件

```
sudo  find  /  -name  nginx*
1
```

##### 8.依依删除4列出的所有文件

```
sudo rm -rf file
1
```

这样就彻底删除nginx了