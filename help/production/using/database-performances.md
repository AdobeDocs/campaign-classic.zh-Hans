---
title: 数据库性能
seo-title: 数据库性能
description: 数据库性能
seo-description: null
page-status-flag: never-activated
uuid: 47ff7532-1fe7-47c2-bc3b-0f46d3a4a288
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 6358c8fd-2b75-4462-acd1-887ee44d3110
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 8%

---


# 数据库性能{#database-performances}

大多数性能问题都与数据库维护相关。 以下是四个主要线索，帮助您找到性能下降的原因：

* 配置,
* 安装和配置Adobe Campaign平台、
* 数据库维护,
* 实时诊断。

## 配置{#configuration}

检查初始Adobe Campaign平台配置是否仍然有效，如有必要，请根据可交付性或数据库大小重新评估客户的需求。 我们还建议运行完整硬件检查（CPU、RAM、IO系统）。

>[!NOTE]
>
>您可以参阅Adobe Campaign [硬件大小调整指南](https://helpx.adobe.com/cn/campaign/kb/hardware-sizing-guide.html) ，以获得洞察。

## 平台配置 {#platform-configuration}

不适当的配置可能会影响平台性能。 我们建议您在serverConf.xml文件中检查网络配置、平台可交付性选 **项和MTA配置** 。

## 数据库维护 {#database-maintenance}

**数据库清理任务**

请确保数据库清理任务可以正常运行。 为此，请视图日志文件，以查看它们是否包含任何错误。 如需详细信息，请参阅[此部分](../../production/using/database-cleanup-workflow.md)。

**维护计划**

确保正确计划和执行数据库维护。 为此，请与数据库管理员联系以进一步了解：

* 维护计划,
* 以前执行的维护计划，
* 视图脚本日志。

如需详细信息，请参阅[此部分](../../production/using/recommendations.md)。

>[!CAUTION]
>
>如果您使用中间源配置，则定期维护数据库至关重要。 在营销平台上分析投放时，营销实例会向中间源实例发送信息。 如果流程放慢，则营销实例将受到影响。

**管理工作表**

请检查工作表的编号和大小。 超过一定大小时，数据库性能会受到影响。 这些表由工作流和投放创建。 工作流和投放处于活动状态时，它们仍保留在数据库中。 要限制工作表的大小，可以执行以下操作：

* 停止或删除具有以下状态的投放: **[!UICONTROL Failed]** 、 **[!UICONTROL In progress]** 、 **[!UICONTROL Ready for delivery]** 或 **[!UICONTROL Paused]** 。
* 停止或删除因错误而暂停的工作流,
* 停止所有用于测试的工作流，这些不包含 **[!UICONTROL End]** 活动，因此其状态保持 **[!UICONTROL Paused]** 不变。

>[!CAUTION]
>
>如果操作耗时长且释放了大量空间，这意味着需要深入的维护（索引重建等）。 如需详细信息，请参阅[此部分](../../production/using/recommendations.md)。

**Adobe Campaign过程监控**

根据Adobe Campaign安装设置，可以使用两种工具进行平台监视：

* 实例生产页面。 For more on this, refer to [Manual monitoring](../../production/using/monitoring-processes.md#manual-monitoring).
* netreport脚本。 有关详细信息，请参阅通过 [Adobe Campaign脚本进行自动监视](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)。

## Specifics {#specifics}

可能需要进行实时诊断以确定问题的原因。 开始，方法是检查进程和平台日志文件，然后在重新创建问题时监视活动库。 请特别注意以下事项：

* 维护执行计划，
* 正在执行的SQL查询,
* 是否同时运行外部进程(清理、导入、聚合计算等)。

