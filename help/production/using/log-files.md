---
title: 日志文件
seo-title: 日志文件
description: 日志文件
seo-description: null
page-status-flag: never-activated
uuid: 266bc067-0218-4b3e-941c-dc5cd0b6a10d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: fac3e3ec-82a7-4087-ba88-2b28b0f69d1c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f018df9a2f7516b92f1f25a757065ef268136a5

---


# 日志文件{#log-files}

日志文件的组织如下：

![](assets/d_ncs_directory.png)

每个 **nlserver** 模块都生成一个保存在以下目录中的日志文件： **`<installation directory>`/var/`<instance>`/log/`<module>`.log **。

nlserver syslogd **** 模块将日志保存到磁盘。 此模块与Unix **syslog守护程序类似**，但已经针对Unix和Windows之间的兼容性进行了调整。 其他Adobe Campaign模块不会将其日志保存到磁盘；他们通过发送UDP包将此任 **务委派给** syslogd模块。

默认情况下，Adobe Campaign平台上安装了 **syslogd** ，但可以使用另一个 **syslog守护程序**。 此模块将在日志目录中创建日 **志文** 件。

多实例模块的日志存储在以下目录中： **`<installation directory>`/var/default/log/**. 所有实例都共享同一日志文件(**例如web.log **)。

其他模块的日志存储在以实例命名的子文件夹中。 每个实例都有其自己的日志文件。

下表列出了多实例日志文件：

| 文件 | 说明 |
|---|---|
| web.log | Web模块日志（客户端控制台、报告、SOAP API等） |
| webmdl.log | 重定向模块中的日志 |
| watchdog.log | Adobe Campaign流程监控模块中的日志 |
| trackinglogd.log | 跟踪日志 |

下表列出了单实例日志文件：

| 文件 | 说明 |
|---|---|
| mta.log | mta模块日志 |
| mtachild.log | 消息传送处理日志 |
| wfserver.log | 工作流服务器模块的日志 |
| runwf.log | 工作流执行日志 |
| inMail.log | 弹回邮件模块日志 |
| logins.log | 记录Adobe Campaign的所有登录尝试（成功与否） |

>[!CAUTION]
>
>redir目 **录仅存** 在于重定向服务器上。 url子 **目录** ，包含要重定向的URL的匹配项，子目录日志 **包含跟** 踪日志。 要生成跟踪日志， **跟踪日志** 模块必须运行。

为了优化性能和存储，logins.log文件被拆分为多个文件，每天一个文件(logins.yy-mm-dd.log)，最多保留365个文件。 syslogd（maxNumberOfLoginsFiles选项）下的serverConf.xml中可以更改&#x200B;**天数** 。 请参阅服务器配置文 [件上的文档](../../installation/using/the-server-configuration-file.md#syslogd)。

默认情况下，每个模块和每个实例的日志限制为两个10 MB文件。 第二个文件称为： **`<modulename>`_2.log **。 因此，每个模块和每个实例的日志大小限制为2*10MB。

但是，您可以保留较大的文件。 要启用此功能，请更改conf/serverConf.xml文件的 **syslogd节点中maxFileSizeMb=&quot;10&quot;** 设置的 **值****** 。 此值表示日志文件的最大大小(MB)。

如果您希望在日志中保留更多的详细信息级别，可以使用 **-verbose参数启动Adobe Campaign模块** :

**nlserver开`<MODULE>`始@`<INSTANCE>`-verbose**
