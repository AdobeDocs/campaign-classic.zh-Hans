---
title: 维护类型
seo-title: 维护类型
description: 维护类型
seo-description: null
page-status-flag: never-activated
uuid: 44faee3d-0549-4f63-8fdc-b24e6de47bc4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 4a436ccf-097c-43e6-9eda-492bada5512a
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 2%

---


# 维护类型{#types-of-maintenance}

## 应用程序维护 {#application-maintenance}

Adobe Campaign提供了一个内置的工作流，它允许您计划特定的数据库维护任务:数据 **库清理工作流**。 此工作流执行以下任务:

* 删除过期记录，
* 删除孤立记录并重新初始化过期对象的状态，
* 更新数据库统计信息。

>[!IMPORTANT]
>
>请注意，清除任务主要处理应用程序级别维护，而不是RDBMS级别维护（统计信息更新除外）。 但是，数据库上需要维护操作。 即使数据库清理工作流成功运行，这并不意味着数据库已得到最佳调整。

## 技术维护 {#technical-maintenance}

数据库清理工作流不包含任何数据库维护工具：由您组织维护。 为此，您可以：

* 与数据库管理员一起使用第三方工具设置数据库维护，
* 使用Adobe Campaign工作流引擎计划和跟踪这些维护活动。

这些维护程序必须定期执行，并应包括：

* 重新为频繁更新的表编制索引，
* 压缩／重建表以避免碎片化。

### 维护计划 {#maintenance-schedule}

您需要找到相应的插槽来执行这些维护活动。 它们在运行或阻止应用程序时（由于锁定）会严重影响数据库性能。

这些任务通常在低活动期间每周运行一次，不会与备份、数据重装或聚合计算相冲突。 一些系统的需求量很大，需要更频繁的维护。

更深入的维护（如完整表重建）可以每月执行一次，最好在应用程序完全停止的情况下执行一次，因为系统仍然不可用。

### 重建表 {#rebuilding-a-table}

提供以下几种策略：

<table> 
 <thead> 
  <tr> 
   <th> 操作 </th> 
   <th> 说明 </th> 
   <th> 优势 </th> 
   <th> 缺点 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 联机碎片整理<br /> </td> 
   <td> 大多数数据库引擎都提供碎片整理方法。<br /> </td> 
   <td> 只需使用数据库碎片整理方法。 这些方法通常通过在碎片整理过程中锁定数据来解决完整性问题。<br /> </td> 
   <td> 根据数据库，这些碎片整理方法可以作为RDBMS选项(Oracle)提供，并不总是处理较大表的最有效方法。<br /> </td> 
  </tr> 
  <tr> 
   <td> 转储和恢复<br /> </td> 
   <td> 将表转储到文件，删除数据库中的表并从转储中恢复。<br /> </td> 
   <td> 这是对表进行碎片整理的最简单方法。 也是数据库几乎已满时的唯一解决方案。<br /> </td> 
   <td> 由于删除并重新创建表，因此即使在只读模式下，应用程序也无法保持联机状态（表在恢复阶段不可用）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 重复、重命名和删除<br /> </td> 
   <td> 这将创建表及其索引的副本，然后删除现有的副本并重命名该副本以代替它。<br /> </td> 
   <td> 此方法比第一种方法快，因为它生成的IO较少（没有作为文件的副本，也没有从此文件中读取）。<br /> </td> 
   <td> 需要两倍的空间量。<br /> 必须停止在进程期间写入表的所有活动进程。 但是，读取过程不会受到影响，因为重建后的最后时刻将交换表。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

