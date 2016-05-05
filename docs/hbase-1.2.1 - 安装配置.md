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
$ chown -R hadoop:hadoop /opt/hbase-1.2.1/
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
### 1. hbase 自带的 hadoop jar
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

### 2. 替换

### 3. 其它依赖包
```
$ cp /opt/hadoop/share/hadoop/common/lib/htrace-core-3.0.4.jar /opt/hbase/lib/
```

## 配置
* conf/hbase-site.xml
```
<configuration>
    <property>
        <name>hbase.rootdir</name>
        <value>hdfs://master:9000/hbase</value>
        <description>The directory shared by RegionServers.</description>
    </property>
    <property>
        <name>hbase.cluster.distributed</name>
        <value>true</value>
        <description>
            The mode the cluster will be in. Possible values are
            false: standalone and pseudo-distributed setups with managed Zookeeper
            true: fully-distributed with unmanaged Zookeeper Quorum (see hbase-env.sh)
        </description>
    </property>
    <property>
        <name>hbase.zookeeper.quorum</name>
        <value>master,slave01,slave02</value>
    </property>
    <property>
        <name>hbase.zookeeper.property.dataDir</name>
        <value>/opt/zookeeper</value>
    </property>
</configuration>
```

* conf/regionservers<br />
将所有的 datanode 添加到这个文件
```
slave01
slave02
```

* zookeeper
```
mkdir -p /opt/zookeeper
chown -R hadoop:hadoop zookeeper
```

## 启动
```
$ /opt/hbase/bin/start-hbase.sh

$ jps
27404 Main
27113 HQuorumPeer
22422 HMaster
22553 HRegionServer
```

## 命令行
```
$ hbase shell

hbase(main):001:0>
hbase(main):001:0> list
```

## UI
http://master:16010/master-status

## 参考文献
* [HBase-1.2.1 集群搭建](http://www.thebigdata.cn/HBase/29894.html)
* [Hadoop2.x下安装HBase](http://my.oschina.net/zc741520/blog/388718)
