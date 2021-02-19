---
solution: Campaign Classic
product: campaign
title: 翻译 Web 窗体
description: 翻译 Web 窗体
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '1565'
ht-degree: 1%

---


# 翻译 Web 窗体{#translating-a-web-form}

可以将Web 应用程序本地化为多种语言。

您可以直接在Adobe Campaign控制台中执行翻译（请参阅[管理编辑器](#managing-translations-in-the-editor)中的翻译），或导出和导入字符串以将翻译外部化（请参阅[将翻译外部化](#externalizing-translation)）。

默认情况下，可用的翻译语言列表在[更改表单显示语言](#changing-forms-display-language)中有详细说明。

Web 应用程序是使用编辑语言设计的：这是用于输入要翻译的标签和其他内容的参考语言。

默认语言是在未将语言设置添加到其访问URL时，Web 应用程序将使用的语言显示。

>[!NOTE]
>
>默认情况下，编辑语言和默认语言与控制台语言相同。

## 选择语言{#choosing-languages}

要定义一种或多种翻译语言，请单击Web 应用程序的&#x200B;**[!UICONTROL Properties]**&#x200B;按钮，然后单击&#x200B;**[!UICONTROL Localization]**&#x200B;选项卡。 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮，为Web 应用程序定义新的翻译语言。

>[!NOTE]
>
>此窗口还允许您更改默认语言和编辑语言。

![](assets/s_ncs_admin_survey_add_lang.png)

当您为Web 应用程序添加翻译语言（或当默认语言和编辑语言不同时）时，**[!UICONTROL Edit]**&#x200B;选项卡中会添加一个&#x200B;**[!UICONTROL Translation]**&#x200B;子选项卡以管理翻译。

Adobe Campaign包括用于翻译和管理多语言翻译的工具。 通过此编辑器，您可以视图要翻译或批准的字符串，直接在界面中输入翻译，或导入/导出字符串以将翻译外部化。

## 在编辑器{#managing-translations-in-the-editor}中管理翻译

### 收集字符串{#collecting-strings}

在&#x200B;**[!UICONTROL Translations]**&#x200B;选项卡中，可以输入构成Web 应用程序的字符串的翻译。

第一次打开此选项卡时，它将不包含任何数据。 单击&#x200B;**[!UICONTROL Collect the strings to translate]**&#x200B;链接以更新Web 应用程序中的字符串。

Adobe Campaign收集所有静态元素的&#x200B;**[!UICONTROL Texts]**&#x200B;选项卡中定义的字段和字符串标签：HTML块、Javascript等 静态元素详见Web表单](../../web/using/static-elements-in-a-web-form.md)中的[静态元素。

![](assets/s_ncs_admin_survey_trad_tab.png)

>[!CAUTION]
>
>此过程可能需要几分钟时间，具体取决于要处理的数据量。
> 
>如果系统词典中出现警告，指出某些翻译缺失，请参阅[转换系统字符串](#translating-the-system-strings)。

每次翻译字符串时，其翻译都会添加到翻译词典中。

当集合进程检测到已存在转换时，此转换将显示在字符串的&#x200B;**[!UICONTROL Text]**&#x200B;列中。 字符串的状态将转换为&#x200B;**[!UICONTROL Translated]**。

对于从未翻译过的字符串，**[!UICONTROL Text]**&#x200B;字段为空，状态为&#x200B;**[!UICONTROL To translate]**。

### 筛选字符串{#filtering-strings}

默认情况下，将显示Web 应用程序的每种翻译语言。 有两种默认过滤器:语言和状态。 单击&#x200B;**[!UICONTROL Filters]**&#x200B;按钮，然后单击&#x200B;**[!UICONTROL By language or status]**&#x200B;以显示匹配的下拉框。 您还可以创建高级过滤器。 有关详细信息，请参见[此页面](../../platform/using/creating-filters.md#creating-an-advanced-filter)。

![](assets/s_ncs_admin_survey_trad_tab_en.png)

转到&#x200B;**[!UICONTROL Language]**&#x200B;下拉框以选择翻译语言。

要仅显示未翻译的字符串，请在&#x200B;**[!UICONTROL Status]**&#x200B;下拉框中选择&#x200B;**[!UICONTROL To translate]**。 您也只能显示已翻译或已批准的字符串。

### 正在翻译字符串{#translating-strings}

1. 要翻译单词，请在字符串的列表上多次单击其行。

   ![](assets/s_ncs_admin_survey_trad_tab_add_term.png)

   源字符串显示在窗口的上部。

1. 在下方输入其翻译。 要批准它，请选中&#x200B;**[!UICONTROL Translation approved]**&#x200B;选项。

   >[!NOTE]
   >
   >翻译批准是可选的，不会阻止该过程。

   未批准的翻译显示为&#x200B;**[!UICONTROL Translated]**。 批准的翻译显示为&#x200B;**[!UICONTROL Approved]**。

## 外部化翻译{#externalizing-translation}

可以使用非Adobe Campaign工具导出和导入字符串来翻译字符串。

>[!CAUTION]
>
>导出字符串后，不要使用集成工具执行任何翻译。 当您重新导入翻译时，这会导致冲突，并且这些翻译将丢失。

### 导出文件{#exporting-files}

1. 选择要导出其字符串的Web 应用程序，右键单击，然后选择&#x200B;**[!UICONTROL Actions > Export strings for translation...]**

   ![](assets/s_ncs_admin_survey_trad_export.png)

1. 选择&#x200B;**[!UICONTROL Export strategy]**:

   * **[!UICONTROL One file per language]**:导出将为每个翻译语言生成一个文件。每个文件对所有选定Web 应用程序都是通用的。
   * **[!UICONTROL One file per Web application]**:导出将为每个选定Web 应用程序生成一个文件。每个文件都包含所有翻译语言。

      >[!NOTE]
      >
      >此类型的导出不适用于XLIFF导出。

   * **[!UICONTROL One file per language and per Web application]**:导出将生成多个文件。每个文件将包含一个翻译语言，每个Web 应用程序。
   * **[!UICONTROL One file for all]**:导出将为所有Web 应用程序生成一个单一的多语言文件。它将包含所有选定Web 应用程序的所有翻译语言。

      >[!NOTE]
      >
      >此类型的导出不适用于XLIFF导出。

1. 然后，选择将记录文件的&#x200B;**[!UICONTROL Target folder]**。
1. 选择文件格式（**[!UICONTROL CSV]**&#x200B;或&#x200B;**[!UICONTROL XLIFF]**），然后单击&#x200B;**[!UICONTROL Start]**。

![](assets/s_ncs_admin_survey_trad_export_start.png)

>[!NOTE]
>
>导出文件的名称将自动生成。 如果多次执行相同导出，您将用新文件替换现有文件。 如果需要保留以前的文件，请更改&#x200B;**[!UICONTROL Target folder]**，然后再次单击&#x200B;**[!UICONTROL Start]**&#x200B;以运行导出。

以&#x200B;**CSV格式**&#x200B;导出文件时，每种语言都链接到状态和批准状态。 **批准？** 列允许您批准翻译。此列可能包含值&#x200B;**Yes**&#x200B;或&#x200B;**No**。 对于集成编辑器（请参阅[管理编辑器](#managing-translations-in-the-editor)中的翻译），批准翻译是可选的，不会阻止该过程。

### 导入文件{#importing-files}

完成外部翻译后，即可导入已翻译的文件。

1. 转到Web 应用程序列表，右键单击，然后选择&#x200B;**[!UICONTROL Actions > Import translated strings...]**

   >[!NOTE]
   >
   >无需选择翻译中涉及的Web 应用程序。 将光标放在Web 应用程序列表的任意位置。

   ![](assets/s_ncs_admin_survey_trad_import.png)

1. 选择要导入的文件，然后单击&#x200B;**[!UICONTROL Upload]**。

   ![](assets/s_ncs_admin_survey_trad_import_start.png)

>[!NOTE]
>
>外部翻译始终优先于内部翻译。 如果发生冲突，内部翻译将被外部翻译覆盖。

## 更改表单显示语言{#changing-forms-display-language}

Web 窗体以在Web 应用程序属性的&#x200B;**[!UICONTROL Localization]**&#x200B;选项卡中指定的默认语言显示。 要更改语言，必须在URL的末尾添加以下字符（其中&#x200B;**xx**&#x200B;是语言的符号）：

```
?lang=xx
```

如果语言是URL的第一个或唯一参数。 例如：**https://myserver/webApp/APP34?lang=en**

```
&lang=xx
```

如果URL中的语言前面有其他参数。 例如：**https://myserver/webApp/APP34?status=1&amp;lang=en**

下面列出了默认提供的翻译语言和词典。

**默认系统词典**:某些语言包含包含系统字符串翻译的默认词典。有关详细信息，请参阅[转换系统字符串](#translating-the-system-strings)。

**日历管理**:Web 应用程序的页面可以包含用于输入日期的日历。默认情况下，此日历提供多种语言（天翻译、日期格式）。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>语言（符号）</strong><br /> </td> 
   <td> <strong>默认系统词典</strong><br /> </td> 
   <td> <strong>日历管理</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 德语(de)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 英语(en)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 英语（美国）(en_US)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 英语（英国）(en_GB)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 阿拉伯语(ar)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 中文(zh)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 朝鲜语(ko)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 丹麦语(da)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 西班牙语(es)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 爱沙尼亚语(et)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 芬兰语(fi)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 法语(fr)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 法语（比利时）(fr_BE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 法语（法国）(fr_FR)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 希腊语(el)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 希伯来语(he)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 匈牙利语(hu)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 印度尼西亚语(id)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 爱尔兰语(ga)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 意大利语(it)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 意大利语（意大利）(it_IT)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 意大利语（瑞士）(it_CH)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 日语(ja)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 拉脱维亚语(lv)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 立陶宛语(lt)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 马耳他语(mt)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 荷兰语(nl)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 荷兰语（比利时）(nl_BE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 荷兰语（荷兰）(nl_NL)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 挪威语（挪威）(no_NO)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 波兰语(pl)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 葡萄牙语(pt)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 葡萄牙语（巴西）(pt_BR)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 葡萄牙语（葡萄牙）(pt_PT)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 俄语(ru)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Slovene(sl)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 斯洛伐克语(sk)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 瑞典语(sv)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 瑞典语（芬兰）(sv_FI)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 瑞典语（瑞典）(sv_SE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 捷克语(cs)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 泰语(th)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 越南语(vi)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 瓦隆(wa)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>要添加默认提供的语言以外的其他语言，请参阅[添加翻译语言](#adding-a-translation-language)

## 示例：显示多种语言的Web 应用程序{#example--displaying-a-web-application-in-several-languages}

以下Web表单有四种语言版本：英语、法语、德语和西班牙语。 所有字符串都已通过Web表单的&#x200B;**[!UICONTROL Translation]**&#x200B;选项卡进行翻译。 由于默认语言是英语，因此在发布调查时，请使用标准URL以英语显示。

![](assets/s_ncs_admin_survey_trad_sample_fr.png)

将&#x200B;**?lang=fr**&#x200B;添加到URL末尾，以法语显示它：

>[!NOTE]
>
>[更改表单显示语言](#changing-forms-display-language)中详细介绍了每种语言的符号列表。

![](assets/s_ncs_admin_survey_trad_sample_en.png)

您可以添加&#x200B;**?lang=es**&#x200B;或&#x200B;**?lang=de**&#x200B;以西班牙语或德语显示它。

>[!NOTE]
>
>如果此Web 应用程序已使用其他参数，请添加&#x200B;**&amp;lang=**。\
>例如：**https://myserver/webApp/APP34?status=1&amp;lang=en**

## 高级转换配置{#advanced-translation-configuration}

>[!CAUTION]
>
>此部分仅面向专家用户。

### 正在翻译系统字符串{#translating-the-system-strings}

系统字符串是所有Web 应用程序使用的现成字符串。 例如：**[!UICONTROL Next]**、**[!UICONTROL Previous]**、**[!UICONTROL Approve]**&#x200B;按钮、**[!UICONTROL Loading]**&#x200B;消息等。 默认情况下，某些语言包含包含这些字符串翻译的词典。 语言列表详见[更改表单显示语言](#changing-forms-display-language)。

如果将Web 应用程序翻译成系统词典未翻译的语言，将显示一条警告消息，通知您某些翻译缺失。

![](assets/s_ncs_admin_survey_trad_error.png)

要添加语言，请应用以下步骤：

1. 转到Adobe Campaign树并单击&#x200B;**[!UICONTROL Administration > Configuration > Global dictionary > System dictionary]**。
1. 在窗口的上部，选择要翻译的系统字符串，然后单击下部的&#x200B;**[!UICONTROL Add]**。

   ![](assets/s_ncs_admin_survey_trad_system_translation.png)

1. 选择翻译语言，然后输入字符串的翻译。 您可以通过选中&#x200B;**[!UICONTROL Translation approved]**&#x200B;选项来批准翻译。

   ![](assets/s_ncs_admin_survey_trad_system_translation2.png)

   >[!NOTE]
   >
   >翻译批准是可选的，不会阻止该过程。

>[!CAUTION]
>
>请勿删除现成系统字符串。

### 添加翻译语言{#adding-a-translation-language}

要将Web 应用程序翻译为默认语言以外的语言（请参阅[更改表单显示语言](#changing-forms-display-language)），您需要添加新的翻译语言。

1. 单击Adobe Campaign树的&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;节点，然后从列表中选择&#x200B;**[!UICONTROL Languages available for translation]**。 可用翻译的列表显示在窗口的下半部分。

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_1.png)

1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮，然后输入&#x200B;**[!UICONTROL Internal name]**、**[!UICONTROL Label]**&#x200B;和图像标识符（标志）。 要添加新映像，请与管理员联系。

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_2.png)

