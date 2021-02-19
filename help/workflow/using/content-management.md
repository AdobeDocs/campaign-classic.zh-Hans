---
solution: Campaign Classic
product: campaign
title: 内容管理
description: 内容管理
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 2%

---


# 内容管理{#content-management}

使用&#x200B;**内容管理**&#x200B;活动，您可以创建和操作内容并基于此内容生成文件。 然后，可以通过“投放”活动提供此内容。

>[!CAUTION]
>
>内容管理是可选的Adobe Campaign模块。 请核实您的许可协议。

活动的属性分为三个步骤：

* **内容选择**:内容可以以前创建过，也可以通过活动创建。
* **内容更新**:任务可以修改内容的主题或导入所有XML内容。
* **操作**:可以保存或生成生成的内容。

   ![](assets/content_mgmt_edit.png)

   有关在Adobe Campaign中配置和使用内容管理的详细信息，请参阅此[部分](../../delivery/using/about-content-management.md)。

1. **内容**

   * **[!UICONTROL Specified in the transition]**

      此选项允许您使用在过渡中指定的内容，即激活内容管理的事件必须包含&#x200B;**[!UICONTROL contentId]**&#x200B;变量。 此变量可由先前的内容管理或任何脚本设置。

   * **[!UICONTROL Explicit]**

      通过此选项，您可以通过&#x200B;**[!UICONTROL Content]**&#x200B;字段选择已创建的内容。 仅当选择&#x200B;**[!UICONTROL Explicit]**&#x200B;选项时，此字段才可见。

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      内容标识符由脚本计算。 通过&#x200B;**[!UICONTROL Script]**&#x200B;字段，可以定义评估内容标识符（主键）的JavaScript模板。 仅当选择&#x200B;**[!UICONTROL Calculated by a script]**&#x200B;选项时，此字段才可见。

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      从发布模板创建新内容。 此新内容将保存在&#x200B;**[!UICONTROL String]**&#x200B;字段中指定的文件中。 **[!UICONTROL Template]**&#x200B;字段指定用于创建内容的发布模板。

      ![](assets/content_mgmt_new.png)

1. **更新内容**

   * **[!UICONTROL Subject]**

      通过此字段，您可以修改内容的主题。

   * **[!UICONTROL Access to data from an XML feed]**

      此选项允许您从通过XSL样式表下载的XML文档中构建内容。 选择此选项后，**[!UICONTROL URL]**&#x200B;字段将指定XML内容下载URL。 使用&#x200B;**[!UICONTROL XSL stylesheet]**&#x200B;可指定要用于转换下载的XML文档的样式表。 此属性是可选的。

      ![](assets/content_mgmt_xmlcontent.png)

1. **要执行的操作**

   * **[!UICONTROL Save]**

      此选项会保存创建或修改的内容。

      出站过渡仅激活一次，内容作为参数保存在&#x200B;**[!UICONTROL contentId]**&#x200B;变量中。

   * **[!UICONTROL Generate]**

      此选项保存内容，然后使用“File”类型发布为每个转换模板生成输出文件。

      ![](assets/content_mgmt_generate.png)

      对于以&#x200B;**[!UICONTROL contentId]**&#x200B;变量中保存的内容的标识符作为其参数和&#x200B;**[!UICONTROL filename]**&#x200B;变量中的文件名生成的每个文件，将激活出站过渡。

## 输入参数{#input-parameters}

* contentId

启用&#x200B;**[!UICONTROL Specified in the transition]**&#x200B;选项时要使用的内容的标识符。

## 输出参数{#output-parameters}

* contentId

   内容标识符。

* 文件名

   如果所选操作为&#x200B;**[!UICONTROL Generate]**，则生成文件的完整名称。

## 示例{#examples}

本[节](../../delivery/using/automating-via-workflows.md#examples)中提供了示例。
