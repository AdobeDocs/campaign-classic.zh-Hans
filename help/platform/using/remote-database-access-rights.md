---
title: 访问外部数据库
seo-title: 访问外部数据库
description: 访问外部数据库
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d2758b5e81d1720a4f01a610e51c4a33995d88d1

---


# 远程数据库访问权限 {#remote-database-access-rights}

首先，为了使用户能够通过FDA对外部数据库执行操作，后者必须在Adobe Campaign中具有特定的名称。

1. 在Adobe **[!UICONTROL Administration > Access Management > Named Rights]** Campaign资源管理器中选择节点。
1. 通过指定所选标签创建新权限。
1. 字段 **[!UICONTROL Name]** 必须采用以下格式 **用户：base@server**，其中：

   * **user** 与外部数据库中用户的名称相对应。
   * **base** 与外部数据库的名称相对应。
   * **server** 对应于外部数据库服务器的名称。

      >[!NOTE]
      >
      >Oracle **中的** :base部件是可选的。

1. 保存指定的右侧，然后从Adobe Campaign浏览器的节 **[!UICONTROL Administration > Access Management > Operators]** 点将其链接到所选用户。

然后，要处理外部数据库中包含的数据，Adobe Campaign用户必须对数据库至少拥有“写入”权限才能创建工作表。 Adobe Campaign会自动删除这些内容。

一般而言，下列权利是必要的：

* **CONNECT**:连接到远程数据库，
* **读取数据**:只读访问包含客户数据的表，
* **阅读“MetaData”**:访问服务器数据目录以获得表结构，
* **加载**:在工作表中成批加载（处理集合和连接时需要）,
* **为TABLE** / **INDEX/PROCEDURE/FUNCTION创建／删除**,
* **说明** （建议）:以便在遇到问题时监控性能，
* **写入数据** （取决于集成方案）。

>[!NOTE]
>
>数据库管理员需要使这些权限与每个数据库引擎的特定权限相匹配。 有关详细信息，请参阅 [RDBMS特定权限](https://docs.campaign.adobe.com/doc/AC6.1/en/technicalResources/technicalResources.html)。