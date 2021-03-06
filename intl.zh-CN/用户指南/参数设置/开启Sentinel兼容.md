# 开启Sentinel兼容 {#task_x1d_nw2_4fb .task}

Sentinel为社区Redis提供高可用服务，云数据库Redis版开发了Sentinel兼容功能，以适应使用了Sentinel的场景。您可以依照本文的说明在云数据库Redis版管理控制台开启该功能。

要使用Sentinel兼容模式，云数据库Redis版实例需满足以下条件：

|限制项|说明|
|---|--|
|引擎版本|Redis 4.0|
|网络类型|VPC|
|前置操作|[开启免密访问](intl.zh-CN/用户指南/管理实例/开启免密访问.md#)|

Redis Sentinel为Redis提供主从实例监控、故障告警、自动故障切换等服务，很多使用本地自建Redis数据库并且对可靠性要求较高的业务场景都用到了Sentinel。为了给这类场景中的Redis数据库迁移上云提供方便，阿里云开发了Sentinel兼容模式。

**说明：** 阿里云云数据库Redis版使用自研的[高可用服务](../../../../intl.zh-CN/产品简介/功能特性.md#)HA组件，无需Sentinel。

1.  登录 [Redis 管理控制台](https://kvstore.console.aliyun.com/)。 
2.  单击目标实例的**实例 ID**或者操作列的**管理**。 
3.  在实例信息页的左侧导航栏中，单击**参数设置**。 
4.  在参数列表中找到\#no\_loose\_sentinel-enabled，单击其操作列的**修改**。 

    **说明：** 如发现有4.0版本的实例不支持该参数，请尝试[升级小版本](intl.zh-CN/用户指南/管理实例/升级小版本.md#)。

5.  在弹出的对话框中将值修改为yes，之后单击**确定**。 

    更多参数信息请参见[参数设置](intl.zh-CN/用户指南/管理实例/参数设置.md#) 。


