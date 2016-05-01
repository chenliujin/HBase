## 版权
* 作者：<a href="http://www.chenliujin.com">陈柳锦</a>
* 主页：<a href="http://www.chenliujin.com">http://www.chenliujin.com</a>
* 邮箱：liujin.chen@qq.com

## Hadoop 版本支持的 HBase 版本
http://hbase.apache.org/book.html#basic.prerequisites

## 环境
* centos 7
* hadoop-2.6.4
* hbase-1.2.1

## 安装
```
$ mv hbase-1.2.1 /opt/
$ cp /opt/
$ ln -s hbase-1.2.1 hbase
```

## 环境变量
```
$ vim /etc/profile
export HBASE_HOME=/opt/hbase
export PATH=$PATH:$HBASE_HOME/bin
```

## 替换 hbase 中自带的 hadoop jar，使用 hadoop-2.6.4 中的 jar
### hbase 自带的 hadoop jar
```
$ find /opt/hbase/lib  -name "hadoop*.jar"

/opt/hbase/lib/hadoop-common-2.5.1.jar
/opt/hbase/lib/hadoop-annotations-2.5.1.jar
/opt/hbase/lib/hadoop-auth-2.5.1.jar
/opt/hbase/lib/hadoop-mapreduce-client-core-2.5.1.jar
/opt/hbase/lib/hadoop-yarn-common-2.5.1.jar
/opt/hbase/lib/hadoop-yarn-api-2.5.1.jar
/opt/hbase/lib/hadoop-hdfs-2.5.1.jar
/opt/hbase/lib/hadoop-client-2.5.1.jar
/opt/hbase/lib/hadoop-mapreduce-client-app-2.5.1.jar
/opt/hbase/lib/hadoop-mapreduce-client-common-2.5.1.jar
/opt/hbase/lib/hadoop-yarn-client-2.5.1.jar
/opt/hbase/lib/hadoop-yarn-server-common-2.5.1.jar
/opt/hbase/lib/hadoop-mapreduce-client-shuffle-2.5.1.jar
/opt/hbase/lib/hadoop-mapreduce-client-jobclient-2.5.1.jar
```

### 替换


## 配置
* hbase-site.xml
```
```

mkdir -p /opt/zookeeper

* regionservers
