---
product: campaign
title: 自定义表情符号列表
description: 了解如何在使用Adobe Campaign Classic时自定义表情符号列表。
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 3%

---

# 自定义表情符号列表 {#customize-emoticons}

弹出窗口中显示的表情符号列表由枚举来规定，该枚举允许您在列表中显示值，以限制用户对给定字段所做的选择。
可以自定义表情符号列表顺序，还可以向列表中添加其他表情符号。
表情符号可用于电子邮件和推送，如需详细信息，请参阅此[页面](defining-the-email-content.md#inserting-emoticons)。

## 添加新表情符号 {#add-new-emoticon}

>[!CAUTION]
>
>表情符号列表不能显示超过81个条目。

1. 选择要从此[页面](https://unicode.org/emoji/charts/full-emoji-list.html)添加的新表情符号。 请注意，它必须与浏览器和操作系统等不同平台兼容。

1. 从&#x200B;**[!UICONTROL Explorer]**&#x200B;中，选择&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]**，然后单击现成枚举。**[!UICONTROL Emoticon list]**

   >[!NOTE]
   >
   >现成的枚举只能由Adobe Campaign Classic控制台的管理员管理。

   ![](assets/emoticon_1.png)

1. 单击 **[!UICONTROL Add]**。

1. 填写以下字段：

   * **[!UICONTROL U+]**:新表情符号的代码。您可以在此[page](https://unicode.org/emoji/charts/full-emoji-list.html)中找到表情符号代码的列表。
为避免出现兼容性问题，我们建议您选择浏览器和每个操作系统都支持的表情符号。

   * **[!UICONTROL Label]**:新表情符号的标签。

   ![](assets/emoticon_5.png)

1. 配置完成后，单击&#x200B;**[!UICONTROL Ok]**，然后单击&#x200B;**[!UICONTROL Save]**。
您的新表情符号将自动放入商店中。

1. 要在投放的&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;窗口中显示该表情符号，请双击该表情符号以选择新创建的表情符号。

1. 在&#x200B;**[!UICONTROL Display order]**&#x200B;下拉菜单中选择，新表情符号的显示顺序。 请注意，通过选择已分配的显示顺序，现有表情符号将自动移至商店。

   <br>在本例中，我们选择了显示顺序号61，这意味着如果某个条目已经具有此顺序，它将被自动移动到商店，而我们的新条目将在枚举列表中占据它的位置。

   ![](assets/emoticon_2.png)

1. 您的新表情符号现已添加到&#x200B;**[!UICONTROL Insert emoticon list]**&#x200B;即装即用枚举中。 您可以随时更改其&#x200B;**[!UICONTROL Display order]**，或在不再需要它时将其移至存储。

1. 要考虑您所做的更改，请断开连接，然后重新连接到Adobe Campaign Classic。 如果新表情符号仍未显示在&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;弹出窗口中，则可能需要清除缓存。 有关更多信息，请参阅此](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)章节[。

1. 现在，您可以在投放中找到新表情符号，该表情符号位于前面步骤中配置的第61位&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;弹出窗口中。 有关如何在投放中使用表情符号的更多信息，请参阅此[页面](defining-the-email-content.md#inserting-emoticons)。

   ![](assets/emoticon_4.png)

1. 如果在&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;弹出窗口中显示以下表情符号，则表示它们配置不正确。 检查&#x200B;**[!UICONTROL U+]**&#x200B;代码或&#x200B;**[!UICONTROL Display order]**&#x200B;在&#x200B;**[!UICONTROL Emoticon list]**&#x200B;中是否正确。

   ![](assets/emoticon_6.png)
