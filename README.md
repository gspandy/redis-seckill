# redis-seckill
## Java 高并发处理秒杀系统

开发环境：IDEA，Tomcat，MySQL，Redis

项目构建：Maven

软件环境：SSM(SpringMVC，Spring，MyBatis) 

项目描述：一套以秒杀商品为目的而搭建制作的高并发系统。基本实现用户根据商家设定的库存量进行秒杀的过程。

技术描述：基于SpringMVC，Spring，MyBatis实现的高并发秒杀系统。代码设计风格基于RESTful，以c3p0作为连接池，Redis数据库为媒介实现高并发技术。

#### 一、业务分析

1.秒杀系统业务流程

![](https://github.com/yangjava/redis-seckill/blob/master/doc/seckill-operation.png)

2.秒杀业务的核心：库存的处理

3.针对库存业务分析：事务（1>.减内存 2>.记录购买明细）

![](https://github.com/yangjava/redis-seckill/blob/master/doc/seckill-operation2.png)

4.记录秒杀成功信息

（1）购买成功的对象

（2）成功的时间/有效期

（3）付款/发货信息

#### 二、异常情况分析

1. 减库存没有记录购买明细

2. 记录明细但没有减库存

3. 出现超卖/少卖

#### 三、难点分析

1. MySQL：事务 + 行级锁

2. 多用户秒杀 ——> Update库存数量

#### 四、功能模块

1. 秒杀接口暴露（Exposer，封装的DTO）

2. 执行秒杀

3. 相关查询

#### 五、开发流程

1. DAO设计编码

2. Service设计编码

3. Web设计编码（restful接口和前端交互等）

4. 高并发优化与分析
