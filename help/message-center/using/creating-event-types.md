---
product: campaign
title: 创建事件类型
description: 了解如何创建与您要在Adobe Campaign Classic中发送的事务型消息匹配的事件类型
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 3%

---

# 创建事件类型 {#creating-event-types}



要确保每个事件都可以更改为个性化消息，您首先需要创建 **事件类型**.

时间 [创建消息模板](../../message-center/using/creating-the-message-template.md)，您将选择与要发送的消息匹配的事件类型。

>[!IMPORTANT]
>
>必须先创建事件类型，然后才能在消息模板中使用它们。

要创建将由Adobe Campaign处理的事件类型，请执行以下步骤：

1. 登录到 **控制实例**.

1. 转到 **[!UICONTROL Administration > Platform > Enumerations]** 树的文件夹。

1. 选择 **[!UICONTROL Event type]** 从名单上。

1. 单击 **[!UICONTROL Add]** 创建枚举值。 这可以是订单确认、密码更改、订单交付更改等。

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >每个事件类型都必须匹配 **[!UICONTROL Event type]** 明细列表。

1. 创建明细列表值后，请注销并重新登录到实例以使创建生效。

>[!NOTE]
>
>了解更多有关明细列表的信息，请参见 [枚举管理](../../platform/using/managing-enumerations.md).


