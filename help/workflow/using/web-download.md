---
product: campaign
title: Web 下载
description: 进一步了解Web下载工作流活动
audience: workflow
content-type: reference
topic-tags: event-activities
exl-id: b6005eae-5fbc-4e22-ab3a-c9b7ed6506f6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 2%

---

# Web 下载{#web-download}

![](../../assets/common.svg)

的 **Web下载** 活动会启动下载显式URL、外部帐户或Adobe Campaign实例上的文件。 使用HTTP协议。 这可以是GET或POST下载。

## 属性 {#properties}

1. **选择Web文件**

   要指定要下载的文件，您可以输入文件URL，使用存储文件的外部HTTP帐户，或通过Adobe Campaign实例加载文件。 可用参数详述如下：

   * 要直接输入要下载的文件的URL，请选择 **[!UICONTROL Explicit URL]** 选项，并在相应的字段中指定URL。 此URL可以使用变量数据构建。

      ![](assets/download_web_edit.png)

   * 使用 **[!UICONTROL External account]**，从下拉列表中选择帐户，然后指定要下载的文件。

      外部帐户是通过 **[!UICONTROL Administration > Platform > External accounts]** Adobe Campaign树的节点。 帐户参数可通过 **[!UICONTROL Edit link]** 图标。

      ![](assets/download_web_edit_external.png)

   * 要从Adobe Campaign实例下载文件，请选择 **[!UICONTROL Adobe Campaign Instance]** 选项。

      ![](assets/download_web_edit_instance.png)

1. **文件历史化**

   的 **[!UICONTROL File historization settings...]** 链接允许您指定文件存储目录和此目录的清除频率。

   ![](assets/download_web_edit_hist.png)

   可以使用以下选项：

   * **[!UICONTROL Use a default storage directory]**:在处理文件之前始终会移动该文件。 如果选中此选项，则文件将移入默认存储目录( **var** Adobe Campaign安装文件夹的目录)。 要指定存储目录，请取消选中方框并在 **[!UICONTROL Storage directory]** 字段
   * **[!UICONTROL Number of files]**:输入存储目录中要保留的最大文件数。
   * **[!UICONTROL Maximum size (in Mb)]**:输入存储目录的最大容量(MB)。

   每个文件在遵守定义的清除规则之前保留24小时。 清除在活动开始之前进行，因此不考虑正在进行的工作流文件。

   文件会根据其年龄（从最早到最新）而删除。 将清除最早的文件，直到验证两个清除规则。 因此，如果定义了100个文件限制，这意味着存储目录将始终包含工作流开始前的100个最新文件，以及正在处理的工作流中正在处理的文件。

   如果您不再想为 **[!UICONTROL Number of files]** 和 **[!UICONTROL Maximum size (in Mb)]** 选项，输入0作为值。

1. **高级参数**

   的 **[!UICONTROL Advanced parameters...]** 链接允许您指定下面显示的其他选项：

   ![](assets/download_web_edit_advanced.png)

   的 **[!UICONTROL Process errors]** 选项的详情，请参阅 [处理错误](monitoring-workflow-execution.md#processing-errors).

## 输出参数 {#output-parameters}

* 文件名：已下载文件的完整名称。
