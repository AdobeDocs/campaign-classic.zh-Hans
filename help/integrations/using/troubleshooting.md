---
product: campaign
title: 故障排除
description: 故障排除
feature: Audiences, People Core Service Integration, Troubleshooting
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: integrations
content-type: reference
topic-tags: audience-sharing
hide: true
exl-id: 61bb184e-affa-430c-8571-56e911cd5a3d
TQID: https://experienceleague.adobe.com/4de9cxyepP-REa2OTWniBFWInphApeUM79sZuFGcynI
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: a39dbcf0-89cb-4765-9bcb-cf9dfbe2875fid: a8512b64-d668-4084-b4f0-34baa899e306
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 136
ht-degree: 3%

---

# 故障排除{#troubleshooting}



如果出现错误，请确保已正确配置以下元素：

* **外部帐户**

  在&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;中，确保正确配置了以下外部SFTP帐户。 提及的SFTP服务器应由您的顾问在Adobe Experience Cloud中进行配置。

   * **[!UICONTROL importSharedAudience]** ：专门用于导入受众的SFTP帐户。
   * **[!UICONTROL exportSharedAudience]** ：专门用于导出受众的SFTP帐户。

* **AMC数据源**

  在&#x200B;**[!UICONTROL Administration > Platform > AMC Data sources]**&#x200B;中，检查是否正确设置了AMC数据源。

在通过Experience Cloud Audience共享受众或导入受众时，可能会丢失某些数据。 只传输ID（“访客ID”或“声明的ID”）能够与用户档案维度协调的记录。 Adobe Campaign无法识别的区段中的ID将不会导入。
