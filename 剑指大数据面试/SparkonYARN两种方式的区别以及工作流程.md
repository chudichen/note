Spark可以和Yarn整合，将Application提交到Yarn上运行，和StandAlone提交模式一样，Yarn也有两种提交任务的方式。

#### 1. yarn-client提交任务方式

##### 执行流程

1. 客户端提交一个Application，在客户端启动一个Driver进程。
2. Driver进程回向RS（ResourceManager）发送请求，启动AM（ApplicationMaster）的资源。
3. RS收到请求，随机选择一台NM（NodeManager）启动AM。这里的NM相当于Standalone中的Worker节点。
4. AM启动后，会向RS请求一批container资源，用于启动Executor。
5. RS会找到一批NM返回给AM，用于启动Executor。
6. AM会向NM发送命令启动Executor。
7. Executor启动后，会反向注册给Driver，Dirver发送task到Executor，执行情况和结果返回给Driver端。

##### 总结

1. Yarn-client模式同样是用于测试，因为Driver运行在本地，Driver会与yarn集群中的Executor进行大量的通信，会造成客户机网卡流量的大量增加。
2. Application Master的作用：为当前Application 申请资源，给NodeManager发送消息启动Executor。
3. **注意**：AM有launchExecutor和申请资源的功能，并没有作业调度的功能。

#### 2. yarn-cluster提交任务方式

##### 执行流程

1. 客户机提交Application应用程序，发送请求到RS（ResourceManager），请求启动AM（ApplicationMaster）。
2. RS收到请求后随机在一台NM（NodeManager）上启动AM（相当于Driver）。
3. AM启动，AM发送请求到RS，请求一批container用于启动Executor。
4. RS返回一批NM节点给AM。
5. Executor反向注册到AM所在的节点的Driver。Driver发送task到Executor。

##### 总结

1. Yarn-Cluster主要用于生产环境中，因为Driver运行在Yarn集群中某一台nodeManager中，每次提交任务的Driver所在的机器都是随机的，不会产生某一台机器网卡流量激增的现象，缺点是任务提交后不能看到日志。只能通过yarn查看日志。

2. ApplicationMaster的作用：当前的Application申请资源给nodeManager发送消息启动Executor。任务调度。（这里和client模式的区别是AM具有调度能力，因为其就是Driver端，包含Driver进程）。

3. 停止集群任务命令：yarn application -kill applicationID

   