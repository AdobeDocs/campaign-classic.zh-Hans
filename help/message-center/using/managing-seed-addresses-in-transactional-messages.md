---
title: 管理交易消息中的种子地址
seo-title: 管理交易消息中的种子地址
description: 管理交易消息中的种子地址
seo-description: null
page-status-flag: never-activated
uuid: 51c4e79d-53bb-4d46-9c7d-e90066f5317d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 12e7043e-e8b5-48a9-8a2f-99e2e6040c3c
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 11%

---


# 管理交易消息中的种子地址{#managing-seed-addresses-in-transactional-messages}

种子地址可让您在发送电子邮件或短信预览之前显示消息的验证、发送投放并测试消息个性化。 种子地址链接到投放，不能用于其他投放。

## 创建种子地址 {#creating-a-seed-address}

1. In the transactional message template, click the **[!UICONTROL Seed addresses]** tab.

   ![](assets/messagecenter_create_seedaddr_001.png)

1. 为其分配标签，以便以后进行选择。

   ![](assets/messagecenter_create_seedaddr_002.png)

1. 输入种子地址(根据通信渠道，使用电子邮件或移动电话)。

   ![](assets/messagecenter_create_seedaddr_003.png)

1. 输入外部标识符:此可选字段允许您输入业务密钥（唯一ID、名称+电子邮件等） 这是您网站上所有用于识别您的用户档案的应用程序所通用的。 如果Adobe Campaign营销数据库中也存在此字段，则您随后可以将事件与数据库中的用户档案进行协调。

   ![](assets/messagecenter_create_seedaddr_003bis.png)

1. 插入测试数据(请参 [阅个性化数据](../../message-center/using/personalization-data.md))。

   ![](assets/messagecenter_create_custo_001.png)

## 创建多个种子地址 {#creating-several-seed-addresses}

1. 单击链 **[!UICONTROL Add other seed addresses]** 接，然后单击 **[!UICONTROL Add]** 按钮。

   ![](assets/messagecenter_create_seedaddr_004.png)

1. 按照创建种子地址部分中详细介绍的 [种子地址配置步骤](#creating-a-seed-address) 。
1. 重复此过程以创建所需数量的地址。

   ![](assets/messagecenter_create_seedaddr_008.png)

创建地址后，您可以显示其预览和个性化。 请参阅 [事务性消息预览](../../message-center/using/transactional-message-preview.md)。
