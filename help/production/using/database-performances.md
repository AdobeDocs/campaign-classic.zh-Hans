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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 34cd6e6cf5652c9e2163848c2b1ef32f53ee6ca4

---


# 数据库性能{#database-performances}

大多数性能问题都与数据库维护相关。 以下是帮助您找到性能下降原因的四个主要线索：

* 配置、
* 安装和配置Adobe Campaign平台、
* 数据库维护，
* 实时诊断。

## 配置 {#configuration}

检查初始Adobe Campaign平台配置是否仍然有效，如有必要，请根据可交付性或数据库大小重新评估客户的需求。 我们还建议运行完整的硬件检查（CPU、RAM、IO系统）。

>[!NOTE]
>
>有关洞察，请参 [阅Adobe Campaign硬件调整指南](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html) 。

## 平台配置 {#platform-configuration}

不适当的配置可能会影响平台性能。 我们建议您检查serverConf.xml文件中的网络配置、平台可交付性选 **项以及MTA配置** 。

## 数据库维护 {#database-maintenance}

**数据库清除任务**

请确保数据库清除任务可运行。 为此，请查看日志文件以查看它们是否包含任何错误。 如需详细信息，请参阅[此部分](../../production/using/database-cleanup-workflow.md)。

**维护计划**

确保正确计划和执行数据库维护。 为此，请与数据库管理员联系以进一步了解：

* 他们的维护计划，
* 以前执行的维护计划，
* 查看脚本日志。

如需详细信息，请参阅[此部分](../../production/using/recommendations.md)。

>[!CAUTION]
>
>如果您使用的是中间采购配置，则定期维护数据库是必不可少的。 在营销平台上分析交付时，营销实例会向中间采购实例发送信息。 如果该流程放慢，则营销实例将受到影响。

**管理工作表**

请检查工作表的数量和大小。 当它们超出某个大小时，数据库性能会受到影响。 这些表由工作流和提交创建。 当工作流和交付处于活动状态时，它们会保留在数据库中。 要限制工作表的大小，可以执行以下操作：

* 停止或删除具有以下状态的提交： **[!UICONTROL Failed]** 、 **[!UICONTROL In progress]** 、 **[!UICONTROL Ready for delivery]** 或 **[!UICONTROL Paused]** 。
* 停止或删除因错误而暂停的工作流，
* 停止所有用于测试的工作流，这些测试不包含活动， **[!UICONTROL End]** 因此其状态仍然保持 **[!UICONTROL Paused]** 。

>[!CAUTION]
>
>如果操作时间长且释放了大量空间，这意味着需要深入的维护（索引重建等）。 如需详细信息，请参阅[此部分](../../production/using/recommendations.md)。

**Adobe Campaign流程监控**

根据Adobe Campaign安装设置，可以使用两种工具进行平台监视：

* 实例生产页面。 For more on this, refer to [Manual monitoring](../../production/using/monitoring-processes.md#manual-monitoring).
* netreport脚本。 有关详细信息，请参阅通 [过Adobe Campaign脚本自动监视](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts)。

## 特定信息 {#specifics}

可能需要运行实时诊断来确定问题的原因。 首先检查进程和平台日志文件，然后在重新创建问题时监控数据库活动。 请特别注意以下事项：

* 维护执行计划，
* 执行SQL查询，
* 是否同时运行外部进程（清理、导入、聚合计算等）。

