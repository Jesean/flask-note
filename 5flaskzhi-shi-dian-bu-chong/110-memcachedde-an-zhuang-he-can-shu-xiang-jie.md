### 安装和启动memcached

1. windows:
   * 安装:memcached -d install
     ```
     32位系统 1.4.4版本：http://static.runoob.com/download/memcached-win32-1.4.4-14.zip
     64位系统 1.4.4版本：http://static.runoob.com/download/memcached-win64-1.4.4-14.zip
     32位系统 1.4.5版本：http://static.runoob.com/download/memcached-1.4.5-x86.zip
     64位系统 1.4.5版本：http://static.runoob.com/download/memcached-1.4.5-amd64.zip
     ```
   * 启动:memcached -d start
   * 停止:memcached.exe -d stop
   * 卸载:memcached.exe -d uninstall
2. linux\(ubuntu\):
   * 安装:sudo apt-get install memcached
   * 启动:sudo service memcached start
3. 可能出现的问题:
   * 提示没有权限:使用管理员权限
   * 不要放在含有中文的路径下面



