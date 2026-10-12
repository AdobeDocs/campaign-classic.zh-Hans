---
product: campaign
title: 测试事务性消息模板
description: 了解如何管理事务性消息中的种子地址，以便在Adobe Campaign Classic中预览和测试它们
feature: Transactional Messaging, Message Center, Templates
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
TQID: 'https://experienceleague.adobe.com/jcmXX4aMPaTBatt4m3s-IAaAeoXnjmPaEE4oqIDoIOI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: baf8e746-117b-5e73-b179-0a83edc0295f
    internal-label: Templates
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 1%
---
# 测试事务性消息模板 {#testing-message-templates}

准备好您的[消息模板](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"}（Campaign v8文档）后，请按照以下步骤预览和测试该模板。

作为从Campaign v7过渡到v8的一部分，Campaign Classic文档集已得到简化和重新组织。 现在，Campaign v8文档集中专门提供了常用功能。 要了解如何添加种子地址、预览事务型消息以及发送校样，请参阅[Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/real-time/transactional-template#test-message-template){target=_blank}。

[![image](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/real-time/transactional-template#test-message-template){target=_blank}

## 个性化数据 {#personalization-data}

可以在消息模板中使用数据来测试事务型消息个性化。 此功能用于生成预览或发送验证。 您还可以为各种Internet访问提供商显示消息的呈现。 有关此内容的详细信息，请参阅[收件箱呈现](../../delivery/using/inbox-rendering.md)。

此数据的目的是在最终投放之前测试您的消息。 这些消息与要处理的实际数据不一致。 但是，XML结构必须与执行实例中存储的事件的结构相同，如下所示：

![](assets/messagecenter_create_custo_006.png)

此信息允许您使用个性化标记个性化消息内容(有关更多信息，请参阅[创建消息内容](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/real-time/transactional-template#create-message-content){target="_blank"}（Campaign v8文档）。

1. 选择事务型消息模板。

1. 在模板中，单击&#x200B;**[!UICONTROL Seed addresses]**&#x200B;选项卡。

1. 在事件内容中，以XML格式输入测试信息。

   ![](assets/messagecenter_create_custo_001.png)

1. 单击 **[!UICONTROL Save]**。
