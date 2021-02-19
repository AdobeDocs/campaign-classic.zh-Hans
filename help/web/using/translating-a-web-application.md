---
solution: Campaign Classic
product: campaign
title: 翻译 Web 应用程序
description: 翻译 Web 应用程序
audience: web
content-type: reference
topic-tags: web-applications
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 5%

---


# 翻译 Web 应用程序{#translating-a-web-application}

您可以翻译使用Web 应用程序数字内容编辑器(数字内容编辑器)创建的Adobe Campaign页面。

如果通过Web 应用程序&#x200B;**[!UICONTROL Properties]**&#x200B;中的&#x200B;**[!UICONTROL Localization]**&#x200B;选项卡至少选择一种其他语言，则在使用数字内容编辑器编辑的页面中添加HTML内容块时，新选项将变为可用。

此选项允许您指示是否必须翻译块内容。

要翻译的字符串与Web 应用程序的其他字符串一样，通过应用程序的&#x200B;**[!UICONTROL Translations]**&#x200B;选项卡进行收集。 有关详细信息，请参见[此页面](../../web/using/translating-a-web-form.md)。

标记要翻译的字符串：

1. 在Web 应用程序中打开使用数字内容编辑器编辑的内容页面。

   ![](assets/dce_translation_3.png)

1. 选择HTML块。
1. 在右侧的参数块中，**[!UICONTROL Localization]**&#x200B;选项允许您标记所选块的内容。 默认情况下，仅翻译页面标题。

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >字符串不能超过1023个字符。

   有三种具体情况：

   * 当所选块包含多个字符串/块时，它将标记为要翻译的单个字符串。 然后，该字符串包含此块中元素的HTML代码。
   * 如果要标记包含多个字符串的块，并且至少已标记其中一个字符串，则会显示警告。 然后，您可以从隔离字符串中删除该标志并添加整个块。

      ![](assets/dce_translation_4.png)

   * 如果要从包含在已标记块中的字符串中删除该标志，则无法直接修改字符串转换选项。 但是，您可以访问包含字符串的块，以便对其进行更改。

      ![](assets/dce_translation_2.png)

1. 标记完字符串后，返回Web 应用程序并选择&#x200B;**[!UICONTROL Translations]**&#x200B;选项卡。
1. 选择 **[!UICONTROL Collect the strings to translate]**。标有数字内容编辑器的字符串将添加到Web 应用程序的字符串。

   >[!NOTE]
   >
   >收集字符串后，如果在列表中删除翻译标志，则不会从数字内容编辑器中删除字符串。 这样，翻译记忆库中就能保留这些字体。

1. 翻译和批准字符串。

   然后，您可以通过从Web 应用程序的&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡中选择所需的语言来预览翻译。

