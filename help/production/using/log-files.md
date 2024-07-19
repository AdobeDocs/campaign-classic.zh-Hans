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

每个&#x200B;**nlserver**&#x200B;模块都生成一个日志文件，该文件保存在以下目录中： **`<installation directory>`/var/`<instance>`/log/`<module>`.log**。

**nlserver syslogd**&#x200B;模块将日志保存到磁盘。 此模块类似于Unix **syslog守护程序**，但已针对Unix和Windows之间的兼容性进行了调整。 其他Adobe Campaign模块不会将其日志保存到磁盘；它们通过发送UDP数据包将此任务委派给&#x200B;**syslogd**&#x200B;模块。

默认情况下，Adobe Campaign平台上安装了&#x200B;**syslogd**&#x200B;模块，但可以使用其他&#x200B;**syslog守护程序**。 此模块在&#x200B;**log**&#x200B;目录中创建日志文件。

多实例模块的日志存储在以下目录中： **`<installation directory>`/var/default/log/**。 所有实例（如&#x200B;**web.log**）共享同一日志文件。

其他模块的日志存储在以实例命名的子文件夹中。 每个实例都有自己的日志文件。

下表列出了多实例日志文件：

| 文件 | 说明 |
|---|---|
| web.log | Web模块日志(客户端控制台、报表、SOAP API等) |
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
>**redir**&#x200B;目录仅存在于重定向服务器上。 **url**&#x200B;子目录包含要重定向的URL的匹配项，而子目录&#x200B;**log**&#x200B;包含跟踪日志。 要生成跟踪日志，必须运行&#x200B;**trackinglogd**&#x200B;模块。

为了优化性能和存储， logins.log文件被拆分为多个文件，每天一个(logins.yy-mm-dd.log)，最多保留365个文件。 在serverConf.xml中，可以在syslogd （**maxNumberOfLoginsFiles**&#x200B;选项）下更改天数。 请参阅有关[服务器配置文件](../../installation/using/the-server-configuration-file.md#syslogd)的文档。

默认情况下，日志限制为每个模块和每个实例两个10 MB的文件。 第二个文件名为： **`<modulename>`_2.log**。 因此，每个模块和每个实例的日志大小限制为2&#42;10 MB。

但是，您可以保留较大的文件。 要启用此功能，请更改&#x200B;**conf/serverConf.xml**&#x200B;文件的&#x200B;**syslogd**&#x200B;节点中的&#x200B;**maxFileSizeMb=&quot;10&quot;**&#x200B;设置的值。 此值表示日志文件的最大大小（以MB为单位）。

如果您想在日志中保留更详细的级别，可以使用&#x200B;**-verbose**&#x200B;参数启动Adobe Campaign模块：

**nlserver启动`<MODULE>`@`<INSTANCE>` -verbose**
