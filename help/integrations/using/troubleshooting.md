---
solution: Campaign Classic
product: campaign
title: 故障排除
description: 故障排除
audience: integrations
content-type: reference
topic-tags: audience-sharing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 3%

---


# 故障排除{#troubleshooting}

如果出错，请确保正确配置了以下元素：

* **外部帐户**

   在&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;中，确保正确配置以下外部SFTP帐户。 顾问应在Adobe Experience Cloud中配置上述SFTP服务器。

   * **[!UICONTROL importSharedAudience]** :专用于导入受众的SFTP帐户。
   * **[!UICONTROL exportSharedAudience]** :专用于导出受众的SFTP帐户。

* **AMC数据源**

   在&#x200B;**[!UICONTROL Administration > Platform > AMC Data sources]**&#x200B;中，检查AMC数据源设置是否正确。

在通过People核心服务共享受众或导入受众时，可能会丢失某些数据。 只传输ID(“访客ID”或“声明ID”)与用户档案维度对帐的记录。 不会导入Adobe Campaign无法识别的People核心服务区段的ID。
