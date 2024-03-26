---
product: campaign
title: 数据库性能
description: 数据库性能
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 33dcfd4b-51fd-44f4-98e0-23eafb79d7da
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 7%

---

# 数据库性能{#database-performances}



大多数性能问题都与数据库维护有关。 以下四个主要线索可帮助您找出性能缓慢的原因：

* 配置
* Adobe Campaign平台的安装和配置
* 数据库维护
* 实时诊断

## 配置 {#configuration}

检查初始Adobe Campaign平台配置是否仍然有效，如有必要，请根据可交付性或数据库大小重新评估客户的需求。 我们还建议运行完整的硬件检查（CPU、RAM、IO系统）。

>[!NOTE]
>
>您可以引用 [Adobe Campaign硬件大小调整指南](https://helpx.adobe.com/cn/campaign/kb/hardware-sizing-guide.html) 以获取见解。

## 平台配置 {#platform-configuration}

配置不当可能会影响平台性能。 我们建议您在中检查网络配置、平台可投放性选项以及MTA配置 **serverConf.xml** 文件。

## 数据库维护 {#database-maintenance}

**数据库清理任务**

请确保数据库清理任务正在运行。 为此，请查看日志文件以查看它们是否包含任何错误。 如需详细信息，请参阅[此小节](../../production/using/database-cleanup-workflow.md)。

**维护计划**

确保正确地计划和执行数据库维护。 要执行此操作，请联系数据库管理员以了解有关以下内容的更多信息：

* 他们的维护计划
* 以前执行的维护计划
* 查看脚本日志

如需详细信息，请参阅[此小节](../../production/using/recommendations.md)。

>[!IMPORTANT]
>
>如果您使用中间源配置，则必须定期维护数据库。 在营销平台上分析投放时，营销实例向中间源实例发送信息。 如果流程速度减慢，则营销实例将受到影响。

**管理工作表**

请检查工作表的数量和大小。 当它们超过一定大小时，数据库性能就会受到影响。 这些表由工作流和投放创建。 当工作流和投放处于活动状态时，它们将保留在数据库中。 要限制工作表的大小，可以执行以下操作：

* 停止或删除具有以下状态的投放： **[!UICONTROL Failed]**， **[!UICONTROL In progress]**， **[!UICONTROL Ready for delivery]**，或 **[!UICONTROL Paused]**.
* 停止或删除由于错误而暂停的工作流。
* 停止所有用于不包含 **[!UICONTROL End]** 活动，因此其地位仍然不变 **[!UICONTROL Paused]**.

>[!IMPORTANT]
>
>如果运行时间较长，并且腾出了大量空间，这就意味着需要进行深入的维护（索引重建等）。 如需详细信息，请参阅[此小节](../../production/using/recommendations.md)。

**Adobe Campaign进程监控**

根据Adobe Campaign安装设置，可以使用两种工具进行平台监控：

* 实例生产页面。 有关详细信息，请参见 [手动监测](../../production/using/monitoring-processes.md#manual-monitoring).
* 此 *网络报告* 脚本。 有关详细信息，请参见 [通过Adobe Campaign脚本自动监控](../../production/using/monitoring-processes.md#automatic-monitoring-via-adobe-campaign-scripts).

## 具体信息 {#specifics}

可能需要运行实时诊断以找出问题的原因。 首先检查流程和平台日志文件，然后在重新创建问题的同时监控数据库活动。 请特别注意以下事项：

* 维护执行计划
* 正在执行的SQL查询
* 外部进程是否同时运行（清理、导入、聚合计算等）。
