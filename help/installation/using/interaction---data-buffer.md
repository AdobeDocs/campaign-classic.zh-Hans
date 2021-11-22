---
product: campaign
title: 互动 - 数据缓冲区
description: 互动 - 数据缓冲区
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---

# 互动 - 数据缓冲区{#interaction-data-buffer}

![](../../assets/v7-only.svg)

您可以通过取消同步优惠建议计算来配置数据缓冲区，以提高入站交互性能。 此配置将在实例自己的配置文件(config-Instance.xml)中执行。

在Adobe Campaign, **数据缓冲区** 已在交互模块中引入。 这样，您就可以 **提高性能** 通过取消同步库存和选件计算来进行入站交互。

它只涉及集客交互，无论是通过调用（包含或不包含调用数据）还是通过状态更新(updateStatus)。

为避免在编写与收件人相关的建议书时出现队列，新进程生成 **数据缓冲区** 能让提案 **异步写入**. 定期读取并清空此数据缓冲区。 默认时段在大约一秒的空间内。因此，建议书编写被分组。

>[!NOTE]
>
>如果您使用与分布式架构的交互，此参数至关重要。

数据缓冲区 **配置** 可以在实例的配置文件(config-Instance.xml)中完成。

>[!CAUTION]
>
>某些配置只能通过Adobe来执行由Adobe托管的部署。 例如，访问服务器和实例配置文件。 要了解有关不同部署的更多信息，请参阅 [托管模型](../../installation/using/hosting-models.md) 或 [本页](../../installation/using/capability-matrix.md).
>
>对配置所做的任何更改都需要重新启动Web服务器(Apache:IIS)和Adobe Campaign进程。\
>配置数据缓冲区后，请确保提供了适用的硬件配置。 （内存量）。


配置数据缓冲区后，请确保提供了适用的硬件配置。 （内存量）。

写入守护程序(进程名为：交互)如下所示：

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

如果您使用Inbound Interaction，则@autostart属性必须为“true”，才能在启动Adobe Campaign服务器时自动启动该进程。

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
