---
product: campaign
title: 交互 — 数据缓冲区
description: 交互 — 数据缓冲区
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 2%

---

# 交互 — 数据缓冲区{#interaction-data-buffer}



您可以通过取消同步优惠建议计算来配置数据缓冲区，以提高入站交互性能。 此配置将在实例自己的配置文件(config-Instance.xml)中执行。

在Adobe Campaign中， **数据缓冲区** 在交互模块中引入。 这允许您 **提高性能** ，方法是取消同步库存和优惠计算。

它只涉及入站交互，无论是通过呼叫（包含或不包含呼叫数据）还是状态更新(updateStatus)。

为了在编写与收件人相关的建议时避免排队，新进程生成 **数据缓冲区** 允许计划书在 **异步写入**. 定期读取和清空此数据缓冲区。 默认时段大约在一秒内。因此，建议书撰写将被分组。

>[!NOTE]
>
>如果您使用分布式架构的交互，此参数是必不可少的。

数据缓冲区 **配置** 可以在实例的配置文件(config-Instance.xml)中完成。

>[!CAUTION]
>
>对于由Adobe托管的部署，某些配置只能由Adobe执行。 例如，访问服务器和实例配置文件。 要了解有关不同部署的更多信息，请参阅 [托管模型](../../installation/using/hosting-models.md) 区域或至 [此页面](../../installation/using/capability-matrix.md).
>
>对配置所做的任何更改都需要重新启动Web服务器(Apache：IIS)和Adobe Campaign进程。\
>配置数据缓冲区后，请确保有合适的硬件配置可用。 （存在的内存量）。


配置数据缓冲区后，请确保有合适的硬件配置可用。 （存在的内存量）。

写入守护进程（名为：交互的进程）的定义如下：

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

如果您使用Inbound Interaction，则@autostart属性必须为“true”，才能在Adobe Campaign服务器启动时自动启动该流程。

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
