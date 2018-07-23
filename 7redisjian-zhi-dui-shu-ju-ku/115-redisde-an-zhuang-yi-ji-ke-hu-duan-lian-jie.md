### redis在Ubuntu系统中的安装与启动

1.安装

```
sudo apt-get install redis-server
```

2.卸载

```
sudo apt-get purge --auto-remove redis-server
```

3.启动:

```
查看是否启动
ps aux|grep redis

手动启动
sudo service redis-server start
```



