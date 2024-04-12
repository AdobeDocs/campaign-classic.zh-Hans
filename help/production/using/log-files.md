---
product: campaign
title: 日志文件
description: 日志文件
feature: Monitoring
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 2%

---

# 日志文件{#log-files}



日志文件的组织方式如下：

![](assets/d_ncs_directory.png)

每个 **nlserver** 模块生成一个日志文件，保存在以下目录中： **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

此 **nlserver syslogd** 模块将日志保存到磁盘。 此模块类似于Unix **syslog守护程序**，但已针对Unix和Windows之间的兼容性进行了调整。 其他Adobe Campaign模块不会将其日志保存到磁盘；而是将此任务委派给 **syslogd** 模块发送UDP数据包。

默认情况下，Adobe Campaign平台具有 **syslogd** 模块已安装，但可以使用另一个 **syslog守护程序**. 此模块在 **日志** 目录。

多实例模块的日志存储在以下目录中： **`<installation directory>`/var/default/log/**. 所有实例都共享同一日志文件(例如， **web.log**)。

其他模块的日志存储在以实例命名的子文件夹中。 每个实例都有自己的日志文件。

下表列出了多实例日志文件：

| 文件 | 说明 |
|---|---|
| web.log | Web模块日志（客户端控制台、报表、SOAP API等） |
| webmdl.log | 重定向模块的日志 |
| watchdog.log | Adobe Campaign流程监控模块的日志 |
| trackinglogd.log | 跟踪日志 |

下表列出了单实例日志文件：

| 文件 | 说明 |
|---|---|
| mta.log | mta模块日志 |
| mtachild.log | 消息投放处理日志 |
| wfserver.log | 工作流服务器模块的日志 |
| runwf.log | 工作流执行日志 |
| inMail.log | 退回邮件模块日志 |
| logins.log | 记录对Adobe Campaign的所有登录尝试（成功与否） |

>[!IMPORTANT]
>
>此 **redir** 目录仅存在于重定向服务器上。 此 **url** 子目录包含要重定向的URL的匹配项，以及子目录 **日志** 包含跟踪日志。 要生成跟踪日志，请 **trackinglogd** 模块必须正在运行。

为了优化性能和存储， logins.log文件被拆分为多个文件，每天一个(logins.yy-mm-dd.log)，最多保留365个文件。 在serverConf.xml中，可以在syslogd (**maxNumberOfLoginsFiles** 选项)。 请参阅有关以下内容的文档 [服务器配置文件](../../installation/using/the-server-configuration-file.md#syslogd).

默认情况下，日志限制为每个模块和每个实例两个10 MB的文件。 第二个文件名为： **`<modulename>`_2.log**. 因此，日志的大小限制为2&#42;每个模块和每个实例10 MB。

但是，您可以保留较大的文件。 要启用此功能，请更改 **maxFileSizeMb=&quot;10&quot;** 在中设置 **syslogd** 节点 **conf/serverConf.xml** 文件。 此值表示日志文件的最大大小（以MB为单位）。

如果您想在日志中保留更详细的信息，可以使用启动Adobe Campaign模块 **-verbose** 参数：

**nlserver start `<MODULE>`@`<INSTANCE>` -verbose**
