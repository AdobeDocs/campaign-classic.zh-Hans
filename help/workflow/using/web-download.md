---
solution: Campaign Classic
product: campaign
title: Web 下载
description: 进一步了解Web下载工作流程活动
audience: workflow
content-type: reference
topic-tags: event-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 2%

---


# Web 下载{#web-download}

Web **下载活动** ，启动在显式URL、外部帐户或Adobe Campaign实例上下载文件。 使用HTTP协议。 这可以是GET或POST下载。

## 属性 {#properties}

1. **选择Web文件**

   要指定要下载的文件，可输入文件URL，使用存储文件的外部HTTP帐户，或通过Adobe Campaign实例加载文件。 可用参数详述如下：

   * 要直接输入要下载的文件的URL，请选 **[!UICONTROL Explicit URL]** 择选项，然后在相应字段中指定URL。 此URL可以使用变量数据构建。

      ![](assets/download_web_edit.png)

   * 要使用 **[!UICONTROL External account]**，请从下拉列表中选择帐户，然后指定要下载的文件。

      外部帐户从Adobe Campaign树 **[!UICONTROL Administration > Platform > External accounts]** 的节点进行配置。 帐户参数可通过图标进行 **[!UICONTROL Edit link]** 编辑。

      ![](assets/download_web_edit_external.png)

   * 要从Adobe Campaign实例下载文件，请选择选 **[!UICONTROL Adobe Campaign Instance]** 项。

      ![](assets/download_web_edit_instance.png)

1. **文件历史化**

   通过 **[!UICONTROL File historization settings...]** 链接可指定文件存储目录和此目录的清除频率。

   ![](assets/download_web_edit_hist.png)

   可以使用以下选项：

   * **[!UICONTROL Use a default storage directory]**:文件在处理前始终被移动。 如果选中此选项，则文件将移入默认存储目录(Adobe Campaign安 **装文** 件夹的vars目录)。 要指定存储目录，请取消选中该框，并在字段中输入其路 **[!UICONTROL Storage directory]** 径
   * **[!UICONTROL Number of files]**:输入要保留在存储目录中的最大文件数。
   * **[!UICONTROL Maximum size (in Mb)]**:输入存储目录的最大容量(MB)。

   每个文件在遵守定义的清除规则之前保存24小时。 清除操作在开始活动之前进行，因此不会考虑正在进行的工作流文件。

   文件会根据其年龄（从最早到最新）而删除。 在验证两个清除规则之前，将清除最旧的文件。 因此，如果定义了100文件限制，这意味着存储目录将始终包含工作流开始之前的100个最新文件，以及正在处理的工作流中正在处理的文件。

   如果不再想为和选项设置 **[!UICONTROL Number of files]** 限 **[!UICONTROL Maximum size (in Mb)]** 制，请输入0作为值。

1. **高级参数**

   通过 **[!UICONTROL Advanced parameters...]** 链接可指定下面显示的其他选项：

   ![](assets/download_web_edit_advanced.png)

   该选项 **[!UICONTROL Process errors]** 在处理错误中 [有详细说明](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

## 输出参数 {#output-parameters}

* 文件名：下载文件的完整名称。
