---
solution: Campaign Classic
product: campaign
title: 自定义表情符号列表
description: 了解如何在使用Adobe Campaign Classic时自定义表情列表。
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 3%

---


# 自定义表情符号列表 {#customize-emoticons}

弹出窗口中显示的表情列表由明细列表来规定，该允许您在列表中显示值以限制用户对给定字段的选择。
可以自定义表情图标列表顺序，还可以向列表添加其他表情图标。
表情图标可通过电子邮件发送，有关更多信息，请参阅本 [页](../../delivery/using/defining-the-email-content.md#inserting-emoticons)。

## 添加新表情图标 {#add-new-emoticon}

>[!CAUTION]
>
>表情图标列表不能显示81个以上的条目。

1. 选择要从此页面添加的新表 [情图标](https://unicode.org/emoji/charts/full-emoji-list.html)。 请注意，它必须与浏览器和操作系统等不同平台兼容。

1. 从中 **[!UICONTROL Explorer]**，选 **[!UICONTROL Administration]** 择 **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** ，然后单 **[!UICONTROL Emoticon list]** 击现成的明细列表。

   >[!NOTE]
   >
   >开箱即用明细列表只能由您的Adobe Campaign Classic控制台的管理员管理。

   ![](assets/emoticon_1.png)

1. 单击 **[!UICONTROL Add]**.

1. 填写以下字段：

   * **[!UICONTROL U+]**:新表情图标的代码。 您可以在此页中找到表情图标代码的 [列表](https://unicode.org/emoji/charts/full-emoji-list.html)。
为避免出现兼容性问题，我们建议您选择浏览器和每个操作系统都支持的表情图标。

   * **[!UICONTROL Label]**:新表情图标的标签。

   ![](assets/emoticon_5.png)

1. 单 **[!UICONTROL Ok]** 击， **[!UICONTROL Save]** 然后完成配置。
您的新表情图标将自动放置在商店中。

1. 要在投放窗口中显 **[!UICONTROL Insert emoticon]** 示表情图标，请通过多次单击来选择新创建的表情图标。

1. 从下拉 **[!UICONTROL Display order]** 列表中选择显示新表情图标的顺序。 请注意，通过选择已分配的显示顺序，现有表情图标将自动移至商店。

   <br>在此示例中，我们选择了显示订单编号61，这意味着如果某个条目已具有此订单，它将自动移至商店，而我们的新条目将在明细列表列表中取代。

   ![](assets/emoticon_2.png)

1. 您的新表情图标现已添 **[!UICONTROL Insert emoticon list]** 加到现成明细列表。 您可以随 **[!UICONTROL Display order]** 时更改它，如果您不再需要它，也可以将其移至商店。

1. 要考虑您所做的更改，请断开连接，然后重新连接到Adobe Campaign Classic。 如果新表情图标仍未出现 **[!UICONTROL Insert emoticon]** 在弹出窗口中，则可能需要清除缓存。 有关更多信息，请参阅此](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)章节[。

1. 您现在可以在投放中的弹出窗口 **[!UICONTROL Insert emoticon]** 中找到新的表情图标，该窗口位于前面步骤中配置的第61位。 有关如何在投放中使用表情图标的详细信息，请参阅本 [页](../../delivery/using/defining-the-email-content.md#inserting-emoticons)。

   ![](assets/emoticon_4.png)

1. 如果弹出窗口中显 **[!UICONTROL Insert emoticon]** 示以下表情图标，则表示它们配置不正确。 检查您的 **[!UICONTROL U+]** 代码 **[!UICONTROL Display order]** 或在中是否正确 **[!UICONTROL Emoticon list]**。

   ![](assets/emoticon_6.png)
