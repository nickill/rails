# rails 安装连接oracle


所需要的gem.

  - [activerecord-oracle_enhanced-adapter](https://github.com/rsim/oracle-enhanced)
  - [ruby-oci8](https://github.com/kubo/ruby-oci8)


###### 一、软件安装
oracle client下载链接链：
[http://www.oracle.com/technetwork/database/features/instant-client/index-097480.html](http://www.oracle.com/technetwork/database/features/instant-client/index-097480.html)


下载解压对应数据库版本的basic sqlplus sdk 安装包

```sh
$ cd /opt/oracle	
$ unzip instantclient-basic-linux.x64-12.2.0.1.0.zip
$ unzip instantclient-sqlplus-linux.x64-12.2.0.1.0.zip
$ unzip instantclient-sdk-linux.x64-12.2.0.1.0.zip
```

创建 libclntsh.so and libocci.so

```sh
$ cd /opt/oracle/instantclient_12_2
$ ln -s libclntsh.so.12.1 libclntsh.so
$ ln -s libocci.so.12.1 libocci.so
```
安装 libaio-dev
```sh
$ sudo apt-get install  libaio-dev
```

###### 二、配置环境变量
修改/etc/profile
```sh
$ sudo vi /etc/profile
export ORACLE_HOME=/opt/instantclient_12_2
export TNS_ADMIN=$ORACLE_HOME
export NLS_LANG=AMERICAN_AMERICA.UTF8
export LD_LIBRARY_PATH=/opt/instantclient_12_2
export PATH=/opt/instantclient_12_2:$PATH
$ source  /etc/profile
```
###### 三、验证
使用sqlplus验证连接连接是否正确
```sh
$ sqlplus username/password@database
```
###### 四、database 配置
配置数据库链接 
```ruby
	 adapter:  'oracle_enhanced',
	 database: '//IP/database',
	 username: 'username',
	 password: 'password'
```

