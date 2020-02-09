---
title: 交互——数据缓冲区
seo-title: 交互——数据缓冲区
description: 交互——数据缓冲区
seo-description: null
page-status-flag: never-activated
uuid: 4cb742b5-6bde-43e8-b26b-16f27dd65f72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: cbfdeb2f-4f20-45b8-8cc0-89362f9ea9c1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 46f5bfb41bfe9c938ac0ffa767ead3e47a32047d

---


# 交互——数据缓冲区{#interaction-data-buffer}

>[!NOTE]
>
>某些配置只能由Adobe为Adobe托管的部署执行。 例如，访问服务器和实例配置文件。 要进一步了解不同的部署，请参阅托 [管模型部分](../../installation/using/hosting-models.md) ，或 [本文](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)。

在Adobe Campaign中，“交 **互”模块中引入了数据缓冲区** 。 这允许您通过取消 **同步库存和选件计算** ，提高入站交互的性能。

它只涉及入站交互，无论是通过呼叫（带有或不带呼叫数据），还是通过状态更新(updateStatus)。

为了避免在编写与接收者相关的建议时出现队列，新进程生成允许异步 **写入建议的数据缓** 冲区 ****。 定期读取和清空此数据缓冲区。 默认时间段在大约一秒的空间内。因此，建议书的编写是分组的。

数据缓冲 **区配置** ，可以在实例的配置文件(config-Instance.xml)中完成。

>[!NOTE]
>
>对配置所做的任何更改都需要重新启动Web服务器(Apache:IIS)和Adobe Campaign进程。\
>配置数据缓冲区后，请确保有适当的硬件配置可用。 （内存量）。

配置数据缓冲区后，请确保有适当的硬件配置可用。 （内存量）。

写入守护程序(进程名为：交互)如下所示：

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

