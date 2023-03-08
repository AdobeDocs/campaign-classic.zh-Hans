---
product: campaign
title: 故障排除
description: 故障排除
audience: integrations
content-type: reference
topic-tags: audience-sharing
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 3%

---

# 故障排除{#troubleshooting}

![](../../assets/common.svg)

如果出现错误，请确保正确配置了以下元素：

* **外部帐户**

   In **[!UICONTROL Administration > Platform > External accounts]**，确保正确配置了以下外部SFTP帐户。 提及的SFTP服务器应由您的顾问在Adobe Experience Cloud中配置。

   * **[!UICONTROL importSharedAudience]** ：专门用于导入受众的SFTP帐户。
   * **[!UICONTROL exportSharedAudience]** ：专门用于导出受众的SFTP帐户。

* **AMC数据源**

   In **[!UICONTROL Administration > Platform > AMC Data sources]**，请检查AMC数据源是否设置正确。

在通过“人员”核心服务共享受众或导入受众时，可能会丢失某些数据。 仅转移ID（“访客ID”或“声明的ID”）能够与配置文件维度协调的记录。 Adobe Campaign无法识别的“人员”核心服务区段中的ID不会导入。
