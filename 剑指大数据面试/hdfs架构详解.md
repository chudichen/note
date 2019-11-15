学习一个新的框架的时候：

1. 百度：搜中文的文章或者文档（**不推荐**）

2. 官网+源码，跪在坚持（**推荐**）

   开源的顶级项目：

   * hadoop.apache.org
   * spark.apache.org
   * flink.apache.org
   * storm.apache.org

hadoop: HDFS/YARN/MapReduce

HDFS:

* NameNode
* DataNode
* SecondNameNode

概念：

* Client

* NameNode：

  * 只有一个

  * metadata：
    * 谁创建的
    * 权限
    * 文件对应的block信息

* DataNode：

  * 多个
  * 存储数据
  * 和NameNode保持心跳（汇报block信息）

* Block: File存入HDFS的时候，是按照block来进行拆分的 默认是128M

