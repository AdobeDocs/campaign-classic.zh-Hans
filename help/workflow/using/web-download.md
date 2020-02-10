---
title: Web下载
seo-title: Web下载
description: Web下载
seo-description: null
page-status-flag: never-activated
uuid: 44039e9c-0cd8-4d3f-b73f-e01c5343835a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 8590cc75-11c8-450d-90e8-56744e12ac70
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cfb1b02a6261c001392b5cc6430f00206e802bb8

---


# Web下载{#web-download}

Web下 **载活动** ，启动在显式URL、外部帐户或Adobe Campaign实例上下载文件。 使用HTTP协议。 这可以是GET或POST下载。

## 属性 {#properties}

1. **选择Web文件**

   要指定要下载的文件，您可以输入文件URL，使用存储文件的外部HTTP帐户，或通过Adobe Campaign实例加载文件。 可用参数详细如下：

   * 要直接输入要下载的文件的URL，请选择该选 **[!UICONTROL Explicit URL]** 项，然后在相应的字段中指定URL。 此URL可以使用变量数据构建。

      ![](assets/download_web_edit.png)

   * 要使用某 **[!UICONTROL External account]**&#x200B;个文件，请从下拉列表中选择帐户，然后指定要下载的文件。

      外部帐户是从Adobe Campaign树 **[!UICONTROL Administration > Platform > External accounts]** 的节点配置的。 帐户参数可以通过图标进行 **[!UICONTROL Edit link]** 编辑。

      ![](assets/download_web_edit_external.png)

   * 要从Adobe Campaign实例下载文件，请选择该 **[!UICONTROL Adobe Campaign Instance]** 选项。

      ![](assets/download_web_edit_instance.png)

1. **文件历史化**

   通过 **[!UICONTROL File historization settings...]** 该链接可指定文件存储目录和此目录的清除频率。

   ![](assets/download_web_edit_hist.png)

   可以使用以下选项：

   * **[!UICONTROL Use a default storage directory]**:在处理文件之前，始终会移动该文件。 如果选中此选项，则文件将移入默认存储目录(Adobe Campaign安装文 **件夹** 的vars目录)。 要指定存储目录，请取消选中该框，然后在字段中输入其路 **[!UICONTROL Storage directory]** 径
   * **[!UICONTROL Number of files]**:输入存储目录中要保存的最大文件数。
   * **[!UICONTROL Maximum size (in Mb)]**:输入存储目录的最大容量（以兆字节为单位）。
   每个文件在遵守定义的清除规则之前保存24小时。 清除操作在活动开始之前进行，因此不考虑进行中的工作流文件。

   文件会根据其年龄（最旧到最新）而删除。 在验证两个清除规则之前，将清除最旧的文件。 因此，如果定义了100个文件限制，这意味着存储目录将始终包含工作流开始之前的100个最新文件，以及正在处理的工作流中的文件。

   如果您不再希望为和选项设置限 **[!UICONTROL Number of files]** 制， **[!UICONTROL Maximum size (in Mb)]** 请输入0作为值。

1. **高级参数**

   通过 **[!UICONTROL Advanced parameters...]** 该链接，您可以指定下面显示的其他选项：

   ![](assets/download_web_edit_advanced.png)

   处理 **[!UICONTROL Process errors]** 错误中详细介绍了 [此选项](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

## 输出参数 {#output-parameters}

* 文件名

   已下载文件的完整名称。

