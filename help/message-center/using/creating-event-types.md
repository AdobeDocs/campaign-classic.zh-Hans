---
product: campaign
title: 创建事件类型
description: 了解如何创建与您要在Adobe Campaign Classic中发送的事务型消息匹配的事件类型
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 3%

---

# 创建事件类型 {#creating-event-types}



为确保每个事件都可以更改为个性化消息，您首先需要创建&#x200B;**事件类型**。

在[创建消息模板](../../message-center/using/creating-the-message-template.md)时，您将选择与要发送的消息匹配的事件类型。

>[!IMPORTANT]
>
>必须先创建事件类型，然后才能在消息模板中使用它们。

要创建将由Adobe Campaign处理的事件类型，请执行以下步骤：

1. 登录到&#x200B;**控件实例**。

1. 转到树的&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;文件夹。

1. 从列表中选择&#x200B;**[!UICONTROL Event type]**。

1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;创建枚举值。 这可以是订单确认、密码更改、订单交付更改等。

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >每个事件类型必须匹配&#x200B;**[!UICONTROL Event type]**&#x200B;枚举中的一个值。

1. 创建明细列表值后，注销并重新登录到实例以使创建生效。

>[!NOTE]
>
>了解有关[枚举管理](../../platform/using/managing-enumerations.md)中明细列表的详细信息。


