---
title: 互动 - 数据缓冲区
seo-title: 互动 - 数据缓冲区
description: 互动 - 数据缓冲区
seo-description: null
page-status-flag: never-activated
uuid: 4cb742b5-6bde-43e8-b26b-16f27dd65f72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: cbfdeb2f-4f20-45b8-8cc0-89362f9ea9c1
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 6%

---


# 互动 - 数据缓冲区{#interaction-data-buffer}

>[!NOTE]
>
>某些配置只能由Adobe执行，以便由Adobe托管。 例如，访问服务器和实例配置文件。 要进一步了解不同的部署，请参 [阅托管模型](../../installation/using/hosting-models.md) 部分或 [本文](https://helpx.adobe.com/cn/campaign/kb/acc-on-prem-vs-hosted.html)。

在Adobe Campaign中， **在交互模块** 中引入了数据缓冲区。 这允许您通过 **取消同步Stock** 和优惠计算来提高入站交互的性能。

它只涉及入站交互，无论是通过呼叫（带有或不带呼叫数据），还是通过状态更新(updateStatus)。

为了在写入与收件人相关的建议时避免队列，新进程生成允许 **异步写入建议** 的数据缓冲区 **区域**。 定期读取并清空此数据缓冲区。 默认时间段在大约一秒的空间内。因此，建议书编写是分组的。

数据缓 **冲区** 配置可以在实例的配置文件(config-Instance.xml)中完成。

>[!NOTE]
>
>对配置所做的任何更改都需要重新启动Web服务器(Apache:IIS)和Adobe Campaign进程。\
>配置数据缓冲区后，请确保提供适合的硬件配置。 （内存量）。

配置数据缓冲区后，请确保提供适合的硬件配置。 （内存量）。

写入守护程序(进程名为：交互)如下：

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

如果您使用“入站交互”，则@autostart属性必须为“true”，才能在Adobe Campaign服务器启动时自动启动该进程。

参数详细信息：

```
 args: Start-up parameters 
 autoStart: Automatic start Default: false 
 callDataSize: Max. number of characters stored in the shared memory for call data
 Default: 0 
 initScript: ID of JavaScript to execute when starting the process 
 maxProcessMemoryAlertMb: Alert concerning the amount of RAM consumed (in Mb) by a given process Default: 1800 
 maxProcessMemoryWarningMb: Warning concerning the amount of RAM consumed (in Mb) by a given process Default: 1600 
 maxSharedEntries: Max. number of events stored in the shared memory. Default: 25000 
 nextOffersSize: Maximum number of eligible offers sorted right after propositions, to be stored for statistics Default: 0 
 processRestartTime: Time of the day when the process is automatically restartedDefault: '06:00:00' 
 runLevel: Priority at start Default: 10 
 targetKeySize: Max. number of characters stored in the shared memory for identifying individuals Default: 16 
```

