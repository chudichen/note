HDFS各个节点的职责：

* Client：发起请求（入口）

* namenode：只有一个，元数据管理，协调工作

* datanode：存储数据，规模1.5W

写流程：

1. 人或者代码发起写数据请求（大小200M）
2. Client发现还需要一些额外的信息：
   * block：128（default）|256
   * replica：1|2|3（recommended）

3. 这些额外的信息在HDFS的配置文件中

4. 根据block大小对源文件进行拆分

5. Client向nameNode发送写请求，nameNode写入metaData

6. namnode按照机架感知返回具体的分配的datanode信息（用于保存数据）

7. Client通过网络向DataNode传数据

8. DataNode互相分配副本

9. 每个block写完，DataNode就会向NameNode发送信息：

   元数据信息：

   * block1： 3 dn1/dn2/dn3
   * block2:    3 dn1/dn2/dn3

读流程：

1. 请求告诉Client
2. Client请求namenode，在metadata中查找文件信息
3. 请求对应的datanode