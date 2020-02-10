---
title: 翻译Web应用程序
seo-title: 翻译Web应用程序
description: 翻译Web应用程序
seo-description: null
page-status-flag: never-activated
uuid: 7b24a872-d3d1-4473-a6f9-96ba2a0eee8b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-applications
discoiquuid: 328e5b2f-8596-4eda-8ac5-57cb29bfb691
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c9c9d5f96856ce9e19571bad032d2bf04eaa60bd

---


# 翻译Web应用程序{#translating-a-web-application}

您可以翻译使用Adobe Campaign数字内容编辑器(DCE)创建的Web应用程序页面。

如果通过Web应用程序的选项卡至少选择 **[!UICONTROL Localization]****[!UICONTROL Properties]** 了一种其他语言，则在使用DCE编辑的页面中添加HTML内容块时，新选项将变为可用。

此选项允许您指示是否必须翻译块内容。

要翻译的字符串通过应用程序的选项卡与Web应用程序的其他字符串收 **[!UICONTROL Translations]** 集的方式相同。 有关详细信息，请参见[此页面](../../web/using/translating-a-web-form.md)。

标记要翻译的字符串：

1. 在Web应用程序中打开使用DCE编辑的内容页面。

   ![](assets/dce_translation_3.png)

1. 选择HTML块。
1. 在右侧的参数块中，通过选 **[!UICONTROL Localization]** 项可标记所选块的内容。 默认情况下，仅翻译页面标题。

   ![](assets/dce_translation_1.png)

   >[!NOTE]
   >
   >字符串不得超过1023个字符。

   有三种具体情况：

   * 当选定的块包含多个字符串／块时，它将标记为一个要翻译的字符串。 然后，该字符串包含该块中元素的HTML代码。
   * 如果要标记包含多个字符串的块，并且至少已标记其中一个字符串，则会显示警告。 然后，您可以从隔离字符串中删除该标志并添加整个块。

      ![](assets/dce_translation_4.png)

   * 如果要从包含在已标记块中的字符串中删除该标志，则不能直接修改字符串转换选项。 但是，您可以访问包含该字符串的块以对其进行更改。

      ![](assets/dce_translation_2.png)

1. 标记完字符串后，返回Web应用程序并选择选 **[!UICONTROL Translations]** 项卡。
1. Select **[!UICONTROL Collect the strings to translate]**. DCE中标记的字符串将添加到Web应用程序的字符串中。

   >[!NOTE]
   >
   >收集字符串后，如果在DCE中删除了转换标志，则不会从列表中删除字符串。 这允许将它们保留在翻译记忆库中。

1. 翻译和批准字符串。

   然后，您可以从Web应用程序的选项卡中选择所需 **[!UICONTROL Preview]** 的语言来预览翻译。

