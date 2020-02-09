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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# 故障排除{#troubleshooting}

如果出错，请确保正确配置了以下元素：

* **外部帐户**

   在中， **[!UICONTROL Administration > Platform > External accounts]**&#x200B;确保正确配置了以下外部SFTP帐户。 您的顾问应已在Adobe Experience cloud中配置上述SFTP服务器。

   * **[!UICONTROL importSharedAudience]** :专用于导入受众的SFTP帐户。
   * **[!UICONTROL exportSharedAudience]** :专用于导出受众的SFTP帐户。

* **AMC数据源**

   在中， **[!UICONTROL Administration > Platform > AMC Data sources]**&#x200B;检查AMC数据源是否设置得当。

在通过“人员”核心服务共享受众或导入受众时，可能会发生一些数据缺失的情况。 只有ID（“访客ID”或“声明ID”）能够与配置文件维度协调的记录才会被传输。 不会导入Adobe Campaign无法识别的People核心服务区段的ID。
