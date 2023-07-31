---
product: campaign
title: 故障排除
description: 故障排除
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 4%

---

# 故障排除{#troubleshooting}



如果出现错误，请确保已正确配置以下元素：

* **外部帐户**

  在 **[!UICONTROL Administration > Platform > External accounts]**，确保正确配置了以下外部SFTP帐户。 提及的SFTP服务器应由您的顾问在Adobe Experience Cloud中进行配置。

   * **[!UICONTROL importSharedAudience]** ：专门用于导入受众的SFTP帐户。
   * **[!UICONTROL exportSharedAudience]** ：专门用于导出受众的SFTP帐户。

* **AMC数据源**

  在 **[!UICONTROL Administration > Platform > AMC Data sources]**，请检查AMC数据源是否设置正确。

在通过People核心服务共享受众或导入受众时，可能会丢失某些数据。 只传输ID（“访客ID”或“声明的ID”）能够与用户档案维度协调的记录。 Adobe Campaign无法识别的People核心服务区段中的ID不会导入。
