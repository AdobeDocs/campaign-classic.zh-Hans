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

弹出窗口中显示的表情列表由明细列表来规则，该允许您在列表中显示值以限制用户对给定字段的选择。
可以自定义表情图标列表顺序，还可以向列表添加其他表情图标。
有关此内容的表情图标可通过电子邮件发送并推送，请参阅此[页面](../../delivery/using/defining-the-email-content.md#inserting-emoticons)。

## 添加新表情图标{#add-new-emoticon}

>[!CAUTION]
>
>表情图标列表不能显示81个以上的条目。

1. 从此[页面](https://unicode.org/emoji/charts/full-emoji-list.html)选择要添加的新表情图标。 请注意，它必须与浏览器和操作系统等不同平台兼容。

1. 在&#x200B;**[!UICONTROL Explorer]**&#x200B;中，选择&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** ，然后单击现成的&#x200B;**[!UICONTROL Emoticon list]**&#x200B;明细列表。

   >[!NOTE]
   >
   >开箱即用的明细列表只能由Adobe Campaign Classic控制台的管理员管理。

   ![](assets/emoticon_1.png)

1. 单击 **[!UICONTROL Add]**.

1. 填写以下字段：

   * **[!UICONTROL U+]**:新表情图标的代码。您可以在此[页面](https://unicode.org/emoji/charts/full-emoji-list.html)中找到表情图标代码的列表。
为避免出现兼容性问题，我们建议您选择浏览器和每个操作系统都支持的表情图标。

   * **[!UICONTROL Label]**:新表情图标的标签。

   ![](assets/emoticon_5.png)

1. 配置完成后，单击&#x200B;**[!UICONTROL Ok]**，然后单击&#x200B;**[!UICONTROL Save]**。
您的新表情图标将自动放入商店。

1. 要在投放的&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;窗口中显示表情图标，请通过多次单击来选择新创建的表情图标。

1. 在&#x200B;**[!UICONTROL Display order]**&#x200B;下拉菜单中进行选择，新表情图标将按顺序显示。 请注意，通过选择已分配的显示顺序，现有表情图标将自动移到商店。

   <br>在此示例中，我们选择了显示订单编号61，这意味着如果某个条目已经拥有此订单，它将自动移至商店，而我们的新条目将在明细列表列表中取代。

   ![](assets/emoticon_2.png)

1. 您的新表情图标现已添加到&#x200B;**[!UICONTROL Insert emoticon list]**&#x200B;现成明细列表。 您可以随时更改其&#x200B;**[!UICONTROL Display order]**，如果不再需要它，则可将其移至商店。

1. 要考虑您所做的更改，请断开连接，然后重新连接Adobe Campaign Classic。 如果您的新表情图标仍未显示在&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;弹出窗口中，您可能需要清除缓存。 有关更多信息，请参阅此](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)章节[。

1. 如前几步中所配置，您现在可以在第61位的&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;弹出窗口中的投放中找到新表情图标。 有关如何在投放中使用表情图标的详细信息，请参阅此[页面](../../delivery/using/defining-the-email-content.md#inserting-emoticons)。

   ![](assets/emoticon_4.png)

1. 如果您的&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;弹出窗口中显示以下表情图标，则表明未正确配置这些表情图标。 检查&#x200B;**[!UICONTROL U+]**&#x200B;代码或&#x200B;**[!UICONTROL Display order]**&#x200B;在&#x200B;**[!UICONTROL Emoticon list]**&#x200B;中是否正确。

   ![](assets/emoticon_6.png)
