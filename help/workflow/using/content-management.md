---
title: 内容管理
seo-title: 内容管理
description: 内容管理
seo-description: null
page-status-flag: never-activated
uuid: 8d1bf84b-96e5-4d3d-9d77-42d2027a74db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 13b72aa1-de40-4548-835b-97e765e04e95
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 内容管理{#content-management}

通过 **内容管理** ，您可以创建和操作内容并基于此内容生成文件。 然后，可以通过“交付”活动交付此内容。

>[!CAUTION]
>
>内容管理是可选的Adobe Campaign模块。 请检查您的许可协议。

活动的属性分为三个步骤：

* **内容选择**:内容可以以前创建过，也可以通过活动创建。
* **内容更新**:该任务可以修改内容的主题或导入所有XML内容。
* **操作**:可以保存或生成生成的内容。

   ![](assets/content_mgmt_edit.png)

   有关在Adobe Campaign中配置和使用内容管理的详细信息，请参阅此 [部分](../../delivery/using/about-content-management.md)。

1. **内容**

   * **[!UICONTROL Specified in the transition]**

      此选项允许您使用在过渡中指定的内容，即激活内容管理的活动必须包含一个变 **[!UICONTROL contentId]** 量。 此变量可以由以前的内容管理或任何脚本设置。

   * **[!UICONTROL Explicit]**

      此选项允许您通过字段选择已创建的内 **[!UICONTROL Content]** 容。 仅当选中该选项时，此字 **[!UICONTROL Explicit]** 段才可见。

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      内容标识符由脚本计算。 通过 **[!UICONTROL Script]** 该字段，可以定义评估内容标识符（主键）的JavaScript模板。 仅当选中该选项时，此字 **[!UICONTROL Calculated by a script]** 段才可见。

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      从发布模板创建新内容。 此新内容将保存在字段中指定的文件 **[!UICONTROL String]** 中。 该字 **[!UICONTROL Template]** 段指定用于创建内容的发布模板。

      ![](assets/content_mgmt_new.png)

1. **更新内容**

   * **[!UICONTROL Subject]**

      通过此字段可修改内容的主题。

   * **[!UICONTROL Access to data from an XML feed]**

      此选项允许您从通过XSL样式表下载的XML文档构建内容。 选择此选项后，该字段 **[!UICONTROL URL]** 将指定XML内容下载URL。 在 **[!UICONTROL XSL stylesheet]** 中可指定用于转换下载的XML文档的样式表。 此属性是可选的。

      ![](assets/content_mgmt_xmlcontent.png)

1. **要执行的操作**

   * **[!UICONTROL Save]**

      此选项会保存创建或修改的内容。

      出站过渡只激活一次，内容将作为参数保存在 **[!UICONTROL contentId]** 变量中。

   * **[!UICONTROL Generate]**

      此选项会保存内容，然后为每个转换模板生成一个“File”类型发布的输出文件。

      ![](assets/content_mgmt_generate.png)

      对于以变量中保存的内容的标识符作为其参数和变量中的文件名生成的每个文件， **[!UICONTROL contentId]** 将激活出站转 **[!UICONTROL filename]** 换。

## 输入参数 {#input-parameters}

* contentId

启用该选项时要使用的内容 **[!UICONTROL Specified in the transition]** 的标识符。

## 输出参数 {#output-parameters}

* contentId

   内容标识符。

* 文件名

   如果选定的操作为，则生成文件的完整名 **[!UICONTROL Generate]**&#x200B;称。

## 示例 {#examples}

本节提供了示 [例](../../delivery/using/automating-via-workflows.md#examples)。
