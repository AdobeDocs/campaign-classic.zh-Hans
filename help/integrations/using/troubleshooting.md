---
title: 故障排除
seo-title: 故障排除
description: 故障排除
seo-description: null
page-status-flag: never-activated
uuid: fb51ad18-221b-4058-b206-ca2ca045c507
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: audience-sharing
discoiquuid: f3ff8c8e-22b0-4d61-9f26-11f5ca3bc0be
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 4%

---


# 故障排除{#troubleshooting}

如果出错，请确保正确配置了以下元素：

* **外部帐户**

   在 **[!UICONTROL Administration > Platform > External accounts]**&#x200B;中，确保正确配置了以下外部SFTP帐户。 上述SFTP服务器应由您的顾问在Adobe Experience Cloud进行配置。

   * **[!UICONTROL importSharedAudience]** :专用于导入受众的SFTP帐户。
   * **[!UICONTROL exportSharedAudience]** :专用于导出受众的SFTP帐户。

* **AMC数据源**

   在 **[!UICONTROL Administration > Platform > AMC Data sources]**&#x200B;中，检查AMC数据源设置是否正确。

在通过People核心服务共享受众或导入受众时，可能会丢失某些数据。 只能传输ID(“访客ID”或“声明ID”)与用户档案维协调的记录。 不会导入Adobe Campaign无法识别的People核心服务区段的ID。
