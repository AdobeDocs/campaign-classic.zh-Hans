---
product: campaign
title: 日志文件
description: 日志文件
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: c9d427da-6965-4945-90f0-d0770701d55e
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 2%

---

# 日志文件{#log-files}



日志文件的组织方式如下：

![](assets/d_ncs_directory.png)

每个 **nlserver** 模块生成保存在以下目录中的日志文件： **`<installation directory>`/var/`<instance>`/log/`<module>`.log**.

的 **nlserver syslogd** 模块将日志保存到磁盘。 此模块类似于Unix **syslog守护程序**，但已针对Unix和Windows之间的兼容性进行了调整。 其他Adobe Campaign模块不会将其日志保存到磁盘；他们将此任务委派给 **syslogd** 模块，方法是发送UDP数据包。

默认情况下，Adobe Campaign平台具有 **syslogd** 安装了模块，但可以使用其他 **syslog守护程序**. 此模块在 **日志** 目录访问Advertising Cloud的帮助。

多实例模块的日志存储在以下目录中： **`<installation directory>`/var/default/log/**. 所有实例(例如， **web.log**)。

其他模块的日志存储在以实例命名的子文件夹中。 每个实例都有其自己的日志文件。

下表列出了多实例日志文件：

| 文件 | 说明 |
|---|---|
| web.log | Web模块日志（客户端控制台、报表、SOAP API等） |
| webmdl.log | 重定向模块中的日志 |
| watchdog.log | 来自Adobe Campaign进程监控模块的日志 |
| trackinglogd.log | 跟踪日志 |

下表列出了单实例日志文件：

| 文件 | 说明 |
|---|---|
| mta.log | mta模块日志 |
| mtachild.log | 消息投放处理日志 |
| wfserver.log | 工作流服务器模块的日志 |
| runwf.log | 工作流执行日志 |
| inMail.log | 退回邮件模块日志 |
| logins.log | 记录所有登录尝试到Adobe Campaign（成功与否） |

>[!IMPORTANT]
>
>的 **redir** 目录仅在重定向服务器上存在。 的 **url** 子目录包含要重定向的URL的匹配项，以及子目录 **日志** 包含跟踪日志。 要生成跟踪日志，请 **trackinglogd** 模块必须正在运行。

为了优化性能和存储， logins.log文件可拆分为多个文件，每天一个文件(logins.yy-mm-dd.log)，最多保留365个文件。 syslogd(**maxNumberOfLoginsFiles** 选项)。 请参阅 [服务器配置文件](../../installation/using/the-server-configuration-file.md#syslogd).

默认情况下，每个模块和每个实例的日志最多可包含两个10 MB的文件。 第二个文件名为： **`<modulename>`_2.log**. 因此，日志大小限制为2&#42;每个模块和每个实例10MB。

但是，您可以保留较大的文件。 要启用此功能，请更改 **maxFileSizeMb=&quot;10&quot;** 设置 **syslogd** 节点 **conf/serverConf.xml** 文件。 此值表示日志文件的最大大小(MB)。

如果您希望在日志中维护更多详细级别，则可以使用 **-verbose** 参数：

**nlserver开始 `<MODULE>`@`<INSTANCE>` -verbose**
