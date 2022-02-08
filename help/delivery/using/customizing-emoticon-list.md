---
product: campaign
title: 自定义表情符号列表
description: 了解如何在使用Adobe Campaign Classic时自定义表情符号列表
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 3%

---

# 自定义表情符号列表 {#customize-emoticons}

![](../../assets/common.svg)

弹出窗口中显示的表情符号列表由枚举来规定，该枚举允许您在列表中显示值，以限制用户对给定字段所做的选择。
可以自定义表情符号列表顺序，还可以向列表中添加其他表情符号。
表情符号可用于电子邮件和推送，有关更多信息，请参阅此 [页面](defining-the-email-content.md#inserting-emoticons).

## 添加新表情符号 {#add-new-emoticon}

>[!CAUTION]
>
>表情符号列表不能显示超过81个条目。

1. 选择要从此处添加的新表情符号 [页面](https://unicode.org/emoji/charts/full-emoji-list.html). 请注意，它必须与浏览器和操作系统等不同平台兼容。

1. 从 **[!UICONTROL Explorer]**，选择 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** ，然后单击 **[!UICONTROL Emoticon list]** 现成枚举。

   >[!NOTE]
   >
   >现成的枚举只能由Adobe Campaign Classic控制台的管理员管理。

   ![](assets/emoticon_1.png)

1. 单击 **[!UICONTROL Add]**。

1. 填写以下字段：

   * **[!UICONTROL U+]**:新表情符号的代码。 您可以在此中找到表情符号代码列表 [页面](https://unicode.org/emoji/charts/full-emoji-list.html).
为避免出现兼容性问题，我们建议您选择浏览器和每个操作系统都支持的表情符号。

   * **[!UICONTROL Label]**:新表情符号的标签。

   ![](assets/emoticon_5.png)

1. 单击 **[!UICONTROL Ok]** then **[!UICONTROL Save]** 配置完成后。
您的新表情符号将自动放入商店中。

1. 要在 **[!UICONTROL Insert emoticon]** 在投放的窗口中，双击新建的表情符号以将其选中。

1. 在 **[!UICONTROL Display order]** 下拉列表，新表情符号的显示顺序。 请注意，通过选择已分配的显示顺序，现有表情符号将自动移至商店。

   <br>在本例中，我们选择了显示顺序号61，这意味着如果某个条目已经具有此顺序，它将被自动移动到商店，而我们的新条目将在枚举列表中占据它的位置。

   ![](assets/emoticon_2.png)

1. 您的新表情符号现已添加到 **[!UICONTROL Insert emoticon list]** 现成枚举。 您可以更改 **[!UICONTROL Display order]** 随时将其移到商店（如果您不再需要）。

1. 要考虑您所做的更改，请断开连接，然后重新连接到Adobe Campaign Classic。 如果您的新表情符号仍未显示在 **[!UICONTROL Insert emoticon]** 弹出窗口，则可能需要清除缓存。 有关更多信息，请参阅此](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)章节[。

1. 现在，您可以在投放的 **[!UICONTROL Insert emoticon]** 在前面步骤中配置的第61位的弹出窗口。 有关如何在投放中使用表情符号的更多信息，请参阅此 [页面](defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. 如果您的 **[!UICONTROL Insert emoticon]** 弹出窗口，这表示它们配置不正确。 检查 **[!UICONTROL U+]** 代码或 **[!UICONTROL Display order]** 在 **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
