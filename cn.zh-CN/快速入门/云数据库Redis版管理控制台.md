# 云数据库Redis版管理控制台 {#concept_xyc_qv5_tdb .concept}

Redis管理控制台是用于管理Redis实例的Web应用程序，您可以通过该控制台上直观的用户界面进行实例创建、网络设置、实例管理、密码设置等操作。

Redis管理控制台是阿里云管理控制台的一部分，关于控制台的通用设置和基本操作请参见[使用阿里云管理控制台](https://www.alibabacloud.com/help/doc-detail/47605.html)。本文将介绍Redis控制台的通用界面，若有差异，请以控制台实际界面为准。

## 前提条件 { .section}

使用阿里云账号登录Redis管理控制台。若没有阿里云账号，请单击[注册](https://account.alibabacloud.com/register/intl_register.html)。

## 控制台简介 { .section}

**控制台首页**

对于Redis所有类型的实例而言，控制台首页的界面信息都是相同的。

登录 [Redis管理控制台](https://kvstore.console.aliyun.com/)，进入**实例列表**页面，如下图所示（仅为示例，请以实际界面为准）。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/3122/1544060957973_zh-CN.png)

实例列表页面中会展示实例ID、状态、已用内存及配额、可用区、创建时间、付费方式、网络类型等信息。

**说明：** 

**已用内存及配额**是由底层系统根据采集信息进行离线汇总得到的结果，存在10分钟左右的延迟，与当前时间的实际值可能存在差别。

**可运维时间段**

您可以在实例信息页面对可运维时间进行修改，阿里云会在可运维时间对实例进行生产维护，维护期间可能会发生闪断，建议您尽量选择业务低峰期为运维时间段。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/3122/1544060957974_zh-CN.png)

## 性能监控 { .section}

单击**实例ID**即可进入实例信息页面，在左侧导航栏中选择**性能监控**查看Redis的历史性能数据，可以查看到不同的监控项。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/3122/1544060957975_zh-CN.png)

单击**性能监控**之后可以查看到不同的监控项，以下对基础监控组的监控项进行说明。

|基础监控项|说明|
|-----|--|
|Keys|后端Redis所有db的key个数的总和，对于集群实例会汇聚后端所有的节点的数据。|
|Expires|当前设置了过期数据的key的个数的总和。|
|ExpiredKeys|历史过期掉的key的个数。这个值是历史过期掉的key的个数的总和，所以是不包含当前设置了过期key同时没有过期掉的值。同时，它是一个历史累加值，不是当前已经过期的key的个数。**说明：** 如果发生主备切换，该值会以新的主库为准。

|
|EvictedKeys|历史淘汰掉的key的个数。这个值是因内存满被淘汰掉的key的历史个数的总和，所以它不是当前每秒淘汰的key的个数。**说明：** 

如果发生主备切换，该值会以新的主库为准。

|
|UsedMemory|当前内存的使用值。由于新建实例时会产生一定的元信息，所以对于主从实例这个值最小是30MB，对于集群实例这个数据的初始值为30MB乘以节点数，最小为200MB。|
|InFlow|后端Redis入口当前每秒的流量值，单位为KBytes/s。|
|OutFlow|后端Redis出口当前每秒的流量值，单位为KBytes/s。|
|FailedCount|对于主从版本，目前这个值没有意义，因为客户端直接连接到后端DB。对于集群版实例，该统计项标识Proxy到Redis的操作失败数目，包括超时、连接断开等异常引起的操作异常的数目。对于部分旧版本的Redis，该值为一个历史值，对于这种情况如果FaileCount没有增加则没有问题。对于新版本，该值为每秒的一个统计均值。后续会都升级成每秒的统计均值。|
|ConnCount|当前Redis的客户端连接个数。|
|TotalQps|当前Redis的每秒操作次数。|
|CpuUsage|当前 Redis 后端的CPU使用率。|

**说明：** 

您可以单击**自定义监控项**添加不同操作命令的访问次数的监控，比如查看set命令每秒的次数。详细信息请参见[性能监控](../../../../intl.zh-CN/用户指南/性能监控.md#)。

## 报警设置 { .section}

选择左侧导航栏的**报警设置**，单击**报警设置**按钮跳转到云监控的设置页面。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/3122/1544060957976_zh-CN.png)

您可以根据指引创建Redis的监控。对于集群实例建议添加所有实例的内存监控，这样可以对集群实例的子节点的内存进行监控，告警设置如下：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/3122/1544060957977_zh-CN.png)

## 参数设置 { .section}

您可以在参数设置页面对Redis的常见参数进行设置，比如淘汰策略及notify-keypsace-events等。详细操作请参见[参数设置](../../../../intl.zh-CN/用户指南/管理实例/参数设置.md#)。

## 备份恢复 { .section}

您可以在备份恢复页面进行备份的设置和克隆实例，另外可以设置自动备份的时间。详细操作请参见[备份与恢复](../../../../intl.zh-CN/用户指南/备份与恢复.md#)。

