调优策略

1. 架构
   * 分表
   * 区间表 partition
   * 中间结果集
   * 压缩

2. 语法
   * 排序 order by / sort by / distribute by / cluster by
   * 控制输出 reduce / partition / task的数量
   * join: 普通join / mapJoin
3. 执行
   * 推测执行
   * 并行执行
   * JVM重用