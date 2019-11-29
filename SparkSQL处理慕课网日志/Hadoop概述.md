##### Hadoop的由来

* 这是一个虚构的名词
* 作者孩子给一只黄棕色大象起的名

#### 什么是Hadoop

* 一个分布式系统的基础架构，由Apache基金会开发。用户可以在不了解分布式底层的情况下，开发分布式应用程序。充分运用集群的分布式计算和存储能力。

* HDFS（Hadoop Distribute File System）
* YARN
* MapReduce

狭义Hadoop VS 广义 Hadoop

* 狭义的Hadoop：是一个适合大数据分布式存储（HDFS）、分布式计算（MapReduce）和资源调度（YARN）的平台。
* 广义的Hadoop：指的是Hadoop的生态系统，是一个非常庞大的概念，Hadoop是其中最基础，最重要的部分。

##### 为什么很多公司使用hadoop作为大数据的解决方案

* 开源，可以对源码进行二次开发
* 社区活跃
* 涉及到分布式存储和计算的方方面面，所需要的东西可以在Hadoop中找到对应的解决方案
* 得了企业的实践和验证

##### 什么是HDFS

* Hadoop实现了一个分布式文件系统简称HDFS
* 源自于Google的GFS论文
* 这篇论文发表于2003年，HDFS是GFS的克隆版

##### HDFS的设计目标

* 非常巨大的分布式文件系统
* 运行在普通的廉价的硬件上
* 易扩展为用户提供性能不错的存储服务

##### HDFS架构

* 1一个Master（NameNode）带N个Slaves（DataNode），HDFS/YARN/HBase
* 1个文件会被拆分成多个Block，通过Block size来决定块的大小

##### NN：

* 负责客户端请求的响应
* 负责元数据（文件名称、副本系数、block存储地址）的管理

DN：

* 存储用户文件对应的数据块（Block）
* 定期向NN发送心跳信息，汇报本身机器所有的Block信息，健康状况。