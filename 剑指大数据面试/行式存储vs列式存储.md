列式存储可以过滤掉无用的列，带来性能的提升

调优策略

1. 架构
   * 分表
   * 分区表 partition
   * 充分利用中间结果集
   * 压缩

2. 语法

   * 排序： order by / sort by / distribute by / cluster by
   * 控制输出（reduce / partition / task）的数量
   * join，普通的join / mapjoin 执行计划

3. 执行

   * 推测执行

   * 并行执行
   * JVM重用

