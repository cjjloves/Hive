# Homework7
##  1. 配置Hive
### 1.1 修改环境变量
在/etc/profile/下增加以下内容
```
#HIVE
export HIVE_HOME=/home/u2/hadoop_installs/hadoop-2.7.4/hive
export PATHA=$PATH:$HIVE_HOME/bin
export JAVA_HOME=/home/u2/java/jdk1.8.0_144
export JRE_HOME=/home/u2/java/jdk1.8.0_144/jre
export CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
export HADOOP_HOME=/home/u2/hadoop_installs/hadoop-2.7.4
```
source /etc/profile 使更改生效
### 1.2 修改hive配置文件
hive文件夹/conf/
复制几个配置文件
```
cp hive-default.xml.template hive-site.xml
cp hive-env.sh.template hive-env.sh
cp hive-log4j2.properties.template hive-log4j2.properties              
cp hive-exec-log4j2.properties.template hive-exec-log4j2.properties
```
修改hive-site.xml
```
#jdbc连接方式
<name>javax.jdo.option.ConnectionDriverName</name>
 <value>com.mysql.jdbc.Driver</value>
#mysql连接配置
<name>javax.jdo.option.ConnectionURL</name>
<value>jdbc:mysql://localhost:3306/hive?createDatabaseIfNotExist=true</value>
#mysql数据库的用户名
   <name>javax.jdo.option.ConnectionUserName</name>
    <value>"mysql用户名"</value>
#用户对应的密码
    <name>javax.jdo.option.ConnectionPassword</name>
    <value>"mysql密码"</value>
    
<property>
    <name>hive.exec.local.scratchdir</name>
    <value>/home/u2/hadoop_installs/hadoop-2.7.4/hive/repertory</value>
    <description>Local scratch space for Hive jobs</description>
  </property>

```
部分配置的参考网站：http://www.jianshu.com/p/978a77a1d6a2
## 2. 运行截图
### 2.1 进入hive
![Image text](https://raw.github.com/cjjloves/Homework7/master/pictures/1.JPG)
### 2.2 查询现有数据库
![Image text](https://raw.github.com/cjjloves/Homework7/master/pictures/2.JPG)
### 2.3 选择数据库default
![Image text](https://raw.github.com/cjjloves/Homework7/master/pictures/3.JPG)
### 2.4 查询default中已存在的表
![Image text](https://raw.github.com/cjjloves/Homework7/master/pictures/4.JPG)
### 2.5 创建表
表名：NewWords。第一列名称为count，类型为int，描述为word_frequency；第二列名称为word,类型为string，描述为word value。两列之间的分隔符为\t  
![Image text](https://raw.github.com/cjjloves/Homework7/master/pictures/5.JPG)
### 2.6 上传txt文件至dfs上
![Image text](https://raw.github.com/cjjloves/Homework7/master/pictures/6.JPG)
### 2.7 将txt文件导入表NewsWord中
![Image text](https://raw.github.com/cjjloves/Homework7/master/pictures/7.JPG)
### 2.8 条件查询
仅当词频大于等于3000时输出  
![Image text](https://raw.github.com/cjjloves/Homework7/master/pictures/8.JPG)  
仅当词频大于等于5000时输出  
![Image text](https://raw.github.com/cjjloves/Homework7/master/pictures/9.JPG)
