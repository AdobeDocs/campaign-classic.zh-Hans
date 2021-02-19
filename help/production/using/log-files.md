---
solution: Campaign Classic
product: campaign
title: 日志文件
description: 日志文件
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 1%

---


# 日志文件{#log-files}

日志文件的组织方式如下：

![](assets/d_ncs_directory.png)

每个&#x200B;**nlserver**&#x200B;模块都生成保存在以下目录中的日志文件：**`<installation directory>`/var/`<instance>`/log/`<module>`.log**。

**nlserver syslogd**&#x200B;模块将日志保存到磁盘。 此模块类似于Unix **syslog守护程序**，但已针对Unix和Windows之间的兼容性进行了调整。 其他Adobe Campaign模块不将日志保存到磁盘；他们通过向&#x200B;**syslogd**&#x200B;模块发送UDP包，将此任务委派给该模块。

默认情况下，Adobe Campaign平台上安装了&#x200B;**syslogd**&#x200B;模块，但可以使用另一个&#x200B;**syslog守护程序**。 此模块在&#x200B;**log**&#x200B;目录中创建日志文件。

多实例模块的日志存储在以下目录中：**`<installation directory>`/var/default/log/**。 所有实例都共享同一日志文件(例如，**web.log**)。

其他模块的日志存储在以实例命名的子文件夹中。 每个实例都有其自己的日志文件。

下表列出了多实例日志文件：

| 文件 | 说明 |
|---|---|
| web.log | Web模块日志（客户端控制台、报告、SOAP API等） |
| webmdl.log | 重定向模块中的日志 |
| watchdog.log | 来自Adobe Campaign进程监视模块的日志 |
| trackinglogd.log | 跟踪日志 |

下表列出了单实例日志文件：

| 文件 | 说明 |
|---|---|
| mta.log | mta模块日志 |
| mtachild.log | 消息投放处理日志 |
| wfserver.log | 工作流服务器模块的日志 |
| runwf.log | 工作流执行日志 |
| inMail.log | 弹回邮件模块日志 |
| logins.log | 记录所有登录尝试以Adobe Campaign（成功与否） |

>[!IMPORTANT]
>
>**redir**&#x200B;目录仅存在于重定向服务器上。 **url**&#x200B;子目录包含要重定向的URL的匹配项，而子目录&#x200B;**log**&#x200B;包含跟踪日志。 要生成跟踪日志,**trackinglogd**&#x200B;模块必须正在运行。

为了优化性能和存储，会将logins.log文件拆分为多个文件，每天一个文件(logins.yy-mm-dd.log)，最多保留365个文件。 syslogd（**maxNumberOfLoginsFiles**&#x200B;选项）下的serverConf.xml中可以更改天数。 请参阅[服务器配置文件](../../installation/using/the-server-configuration-file.md#syslogd)上的文档。

默认情况下，每个模块和每个实例的日志限制为两个10 MB文件。 第二个文件称为：**`<modulename>`_2.log**。 因此，每个模块和每个实例的日志大小限制为2*10MB。

但是，您可以保留较大的文件。 要启用此功能，请更改&#x200B;**conf/serverConf.xml**&#x200B;文件&#x200B;**syslogd**&#x200B;节点中&#x200B;**maxFileSizeMb=&quot;10&quot;**&#x200B;设置的值。 此值表示日志文件的最大大小(MB)。

如果希望在日志中保留更多详细级别，可以使用&#x200B;**-verbose**&#x200B;参数开始Adobe Campaign模块：

**nlserver开始 `<MODULE>`@`<INSTANCE>` -verbose**
