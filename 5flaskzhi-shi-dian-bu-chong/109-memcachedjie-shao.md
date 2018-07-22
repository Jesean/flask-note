## memcached

### 什么是memcached:

1. memcached之前是danga的一个项目，最早是为LiveJournal服务的，当初设计师为了加速LiveJournal访问速度而开发的，后来被很多大型项目采用。官网是www.danga.com或者是memcached.org
2. Memcached是一个高性能的分布式的内存对象缓存系统，全世界有不少公司采用这个缓存项目来构建大负载的网站，来分担数据库的压力。Memcached是通过在内存里维护一个巨大的hash表，memcached能存储各种各样的数据，包括图像、视频、文件、以及数据库检索的结果等。简单的说就是将数据调用到内存中，然后从内存中读取，从而大大提高读取速度
3. 哪些情况下适合使用Memcached:存储验证码\(图形验证码，短信验证码\)、登录session等所有不是至关重要的数据。

### 安装和启动memcached

1. windows:
   * 安装:memcached -d install
   * 启动:memcached -d start
2. linux\(ubuntu\):
   * 安装:sudo apt-get install memcached
   * 启动:sudo service memcached start
3. 可能出现的问题:
   * 提示没有权限:使用管理员权限
   * 不要放在含有中文的路径下面



