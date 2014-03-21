# CHANGE MYSQL PRIVILEGE
1.连接进入；

  mysql -u root -proot(这里密码在mysql安装过程中提示有设置)

2.我这里直接给root的外部访问权限了；

grant all privileges on *.* to ‘root’@'%’ identified by ‘passwordd’ with grant option;

赋予root用户针对数据库的全部权限。（password为root用户密码）

3.退出数据库。

这时在Windows下面远程连接该数据库，则会报
Can’t connect to MySQL server on ‘xxx.xxx.xxx.xxx’的错误。

此错误原因在于：
ubuntu中MySQL监听的3306端口IP问题，查看ubuntu中3306端口监听

**netstat -anpt|grep 3306**

可以发现，当前默认监听的是127.0.0.1:3306

这里修改127.0.0.1的ip地址为你当前的ip地址。
使用root权限，修改/etc/mysql/my.cnf文件中bind-address，将bind-address=127.0.0.1修改为本机IP，重启MySQL服务，再使用上面命令查看端口监听，就会发现已经变成了本机IP:3306。这时，就可以使用远程连接了。