---
product: campaign
title: 维护类型
description: 维护类型
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 2%

---

# 维护类型{#types-of-maintenance}



## 应用程序维护 {#application-maintenance}

Adobe Campaign提供了一个内置工作流，可让您计划特定数据库维护任务：the **数据库清理工作流**. 此工作流会执行以下任务：

* 删除过期记录，
* 删除孤立记录并重新初始化过期对象的状态，
* 更新数据库统计信息。

>[!IMPORTANT]
>
>请注意，清理任务主要涉及应用程序级别维护，而不涉及RDBMS级别维护（统计更新除外）。 但是，需要对数据库执行维护操作。 即使数据库清理工作流成功运行，这并不意味着数据库已得到最佳调整。

## 技术维护 {#technical-maintenance}

数据库清理工作流不包含任何数据库维护工具：由您组织维护。 为此，您可以：

* 与数据库管理员合作，使用第三方工具设置数据库维护，
* 使用Adobe Campaign工作流引擎计划和跟踪这些维护活动。

这些维护程序必须定期执行，并应包括以下内容：

* 重新索引频繁更新的表，
* 压缩/重建表以避免碎片化。

### 维护计划 {#maintenance-schedule}

您需要找到执行这些维护活动的适当插槽。 它们在运行时会严重影响数据库性能，甚至会阻止应用程序（由于锁定）。

这些任务通常在低活动期间每周运行一次，不会与备份、数据重新加载或聚合计算相冲突。 有些系统的维护要求较高。

更深入的维护（如完整表重建）可每月执行一次，最好是在应用程序完全停止时执行，因为系统仍然不可用。

### 重建表 {#rebuilding-a-table}

提供了以下几种策略：

<table> 
 <thead> 
  <tr> 
   <th> 操作 </th> 
   <th> 说明 </th> 
   <th> 好处 </th> 
   <th> 缺点 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 联机碎片整理<br /> </td> 
   <td> 大多数数据库引擎提供碎片整理方法。<br /> </td> 
   <td> 只需使用数据库碎片整理方法即可。 这些方法通常在碎片整理期间通过锁定数据来解决完整性问题。<br /> </td> 
   <td> 根据数据库的不同，这些碎片整理方法可以作为RDBMS选项(Oracle)提供，并且并不总是处理较大表的最有效方法。<br /> </td> 
  </tr> 
  <tr> 
   <td> 转储和恢复<br /> </td> 
   <td> 将表转储到文件中，删除数据库中的表，并从转储中恢复。<br /> </td> 
   <td> 这是对表进行碎片整理的最简单方法。 也是数据库几乎已满时的唯一解决方案。<br /> </td> 
   <td> 由于表被删除并重新创建，因此即使在只读模式下，应用程序也无法保持联机状态（表在恢复阶段期间不可用）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 复制、重命名和删除<br /> </td> 
   <td> 这会创建表及其索引的副本，然后删除现有副本并重命名副本以替换它。<br /> </td> 
   <td> 此方法比第一种方法速度更快，因为它生成的IO较少（没有作为文件的副本，也没有从此文件中读取）。<br /> </td> 
   <td> 需要两倍的空间。<br /> 必须停止在进程期间写入表的所有活动进程。 但是，读取过程不会受到影响，因为表在重建后的最后时刻被交换。 <br /> </td> 
  </tr> 
 </tbody> 
</table>
