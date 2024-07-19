---
product: campaign
title: 维护类型
description: 维护类型
feature: Monitoring
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 2%

---

# 维护类型{#types-of-maintenance}



## 应用程序维护 {#application-maintenance}

Adobe Campaign提供了一个内置的工作流，可让您计划某些数据库维护任务： **数据库清理工作流**。 此工作流会执行以下任务：

* 删除过期的记录，
* 删除孤立的记录和重新初始化过期对象，
* 更新数据库统计信息。

>[!IMPORTANT]
>
>请注意，清理任务主要涉及应用程序级别的维护，而不是RDBMS级别的维护（统计信息更新除外）。 但是，需要对数据库进行维护操作。 即使数据库清理工作流成功运行，这并不意味着数据库得到了最佳优化。

## 技术维护 {#technical-maintenance}

数据库清理工作流不包括任何数据库维护工具：由您来组织维护。 为此，您可以：

* 与您的数据库管理员合作，使用第三方工具设置数据库维护，
* 使用Adobe Campaign工作流引擎来计划和跟踪这些维护活动。

这些维护程序必须定期执行，并应包括以下内容：

* 重新索引经常更新的表，
* 压缩/重建表以避免碎片。

### 维护计划 {#maintenance-schedule}

您需要找到适合执行这些维护活动的版块。 它们可能会严重影响运行时的数据库性能，甚至会阻止应用程序（由于锁定）。

这些任务通常在活动较少期间每周运行一次，不会与备份、数据重新加载或聚合计算发生冲突。 有些系统要求频繁维护。

更深入的维护，如完全表重建，可以每月执行一次，最好是应用程序完全停止，因为系统无论如何都不可用。

### 重建表 {#rebuilding-a-table}

有几种策略可供使用：

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
   <td> 大多数数据库引擎都提供碎片整理方法。<br /> </td> 
   <td> 只需使用数据库碎片整理方法即可。 这些方法通常通过在碎片整理期间锁定数据来解决完整性问题。<br /> </td> 
   <td> 根据数据库的不同，这些碎片整理方法可以作为RDBMS选项(Oracle)提供，并且并不总是处理较大表的最有效方法。<br /> </td> 
  </tr> 
  <tr> 
   <td> 转储和还原<br /> </td> 
   <td> 将表转储到文件，删除数据库中的表并从转储中还原。<br /> </td> 
   <td> 这是对表进行碎片整理的最简单方法。 也是数据库几乎已满时的唯一解决方案。<br /> </td> 
   <td> 由于表已被删除并重新创建，因此即使处于只读模式（在还原阶段表不可用），应用程序也无法保持联机。<br /> </td> 
  </tr> 
  <tr> 
   <td> 复制、重命名和删除<br /> </td> 
   <td> 这将创建表及其索引的副本，然后删除现有副本，并重命名副本以替换现有副本。<br /> </td> 
   <td> 此方法比第一种方法速度快，因为它生成的IO较少（没有作为文件并从此文件读取的副本）。<br /> </td> 
   <td> 需要两倍的空间量。<br />必须停止在进程中写入表的所有活动进程。 但是，读取过程不会受到影响，因为表格在重建后的最后时刻会被交换。<br /> </td> 
  </tr> 
 </tbody> 
</table>
