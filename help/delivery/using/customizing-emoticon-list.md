---
product: campaign
title: 自定义表情符号列表
description: 了解在使用Adobe Campaign时如何自定义表情符号列表
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Email, Push
role: User, Data Engineer
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: 287d1bf60b39e9e2b389701097995dbea962dec9
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 3%

---

# 自定义表情符号列表 {#customize-emoticons}

弹出式窗口中显示的表情符号列表由枚举规则，允许您在列表中显示值，以限制用户对给定字段的选择。
表情符号列表顺序可以自定义，您也可以向列表添加其他表情符号。

请注意，表情符号仅可用于电子邮件和推送。 有关详细信息，请参阅此[页面](defining-the-email-content.md#inserting-emoticons)。

## 添加新表情符号 {#add-new-emoticon}

>[!CAUTION]
>
>表情符号列表不能显示超过81个条目。

1. 从此[页面](https://unicode.org/emoji/charts/full-emoji-list.html)中选择要添加的新表情符号。 请注意，它必须与不同的平台（如浏览器和操作系统）兼容。

1. 从&#x200B;**[!UICONTROL Explorer]**&#x200B;中，选择&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]**，然后单击&#x200B;**[!UICONTROL Emoticon list]**&#x200B;现成的枚举。

   >[!NOTE]
   >
   >现成的枚举只能由Adobe Campaign Classic控制台的管理员管理。

   ![](assets/emoticon_1.png)

1. 单击 **[!UICONTROL Add]**。

1. 填写以下字段：

   * **[!UICONTROL U+]**：您的新表情符号的代码。 您可以在此[页面](https://unicode.org/emoji/charts/full-emoji-list.html)中找到表情符号代码列表。
为避免出现兼容性问题，我们建议您选择在浏览器和每个操作系统上支持的表情符号。

   * **[!UICONTROL Label]**：您新表情符号的标签。

   ![](assets/emoticon_5.png)

1. 配置完成后，单击&#x200B;**[!UICONTROL Ok]**，然后单击&#x200B;**[!UICONTROL Save]**。
你的新表情符号会自动放在商店里。

1. 若要在投放的&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;窗口中显示表情符号，请双击该表情符号以将其选中。

1. 在&#x200B;**[!UICONTROL Display order]**&#x200B;下拉菜单中选择新表情符号的显示顺序。 请注意，通过选择已分配的显示顺序，现有表情符号将自动移至商店。

   <br>在本例中，我们选择了显示订单号61，这意味着如果某个条目已具有此订单，则它会自动移至商店，并且我们的新条目将在枚举列表中占据其位置。

   ![](assets/emoticon_2.png)

1. 您的新表情符号现已添加到&#x200B;**[!UICONTROL Insert emoticon list]**&#x200B;现成枚举。 您可以随时更改其&#x200B;**[!UICONTROL Display order]**，如果不再需要它，可将其移至商店。

1. 要考虑您的更改，请断开连接，然后重新与Adobe Campaign Classic连接。 如果新的表情符号仍未出现在&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;弹出窗口中，您可能需要清除缓存。 有关更多信息，请参阅此](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)章节[。

1. 现在，您可以在投放的第61个位置的&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;弹出窗口中找到新表情符号，如前面的步骤中所配置。 有关如何在投放中使用表情符号的更多信息，请参阅此[页面](defining-the-email-content.md#inserting-emoticons)。

   ![](assets/emoticon_4.png)

1. 如果&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;弹出窗口中显示以下表情符号，则表示未正确配置这些表情符号。 检查&#x200B;**[!UICONTROL Emoticon list]**&#x200B;中您的&#x200B;**[!UICONTROL U+]**&#x200B;代码或&#x200B;**[!UICONTROL Display order]**&#x200B;是否正确。

   ![](assets/emoticon_6.png)
