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

**Web下载**&#x200B;活动会启动下载显式URL、外部帐户或Adobe Campaign实例上的文件。 使用HTTP协议。 这可以是GET或POST下载。

## 属性 {#properties}

1. **选择Web文件**

   要指定要下载的文件，您可以输入文件URL，使用存储文件的外部HTTP帐户，或通过Adobe Campaign实例加载文件。 可用参数详述如下：

   * 要直接输入要下载的文件的URL，请选择&#x200B;**[!UICONTROL Explicit URL]**&#x200B;选项，然后在相应的字段中指定该URL。 此URL可以使用变量数据构建。

      ![](assets/download_web_edit.png)

   * 要使用&#x200B;**[!UICONTROL External account]**，请从下拉列表中选择帐户，然后指定要下载的文件。

      从Adobe Campaign树的&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;节点配置外部帐户。 可以通过&#x200B;**[!UICONTROL Edit link]**&#x200B;图标编辑帐户参数。

      ![](assets/download_web_edit_external.png)

   * 要从Adobe Campaign实例下载文件，请选择&#x200B;**[!UICONTROL Adobe Campaign Instance]**&#x200B;选项。

      ![](assets/download_web_edit_instance.png)

1. **文件历史化**

   **[!UICONTROL File historization settings...]**&#x200B;链接允许您指定文件存储目录和此目录的清除频率。

   ![](assets/download_web_edit_hist.png)

   可以使用以下选项：

   * **[!UICONTROL Use a default storage directory]**:在处理文件之前始终会移动该文件。如果选中此选项，则文件将移入默认存储目录(Adobe Campaign安装文件夹的&#x200B;**vars**&#x200B;目录)。 要指定存储目录，请取消选中该框，并在&#x200B;**[!UICONTROL Storage directory]**&#x200B;字段中输入其路径
   * **[!UICONTROL Number of files]**:输入存储目录中要保留的最大文件数。
   * **[!UICONTROL Maximum size (in Mb)]**:输入存储目录的最大容量(MB)。

   每个文件在遵守定义的清除规则之前保留24小时。 清除在活动开始之前进行，因此不考虑正在进行的工作流文件。

   文件会根据其年龄（从最早到最新）而删除。 将清除最早的文件，直到验证两个清除规则。 因此，如果定义了100个文件限制，这意味着存储目录将始终包含工作流开始前的100个最新文件，以及正在处理的工作流中正在处理的文件。

   如果不再想为&#x200B;**[!UICONTROL Number of files]**&#x200B;和&#x200B;**[!UICONTROL Maximum size (in Mb)]**&#x200B;选项设置限制，请输入0作为值。

1. **高级参数**

   **[!UICONTROL Advanced parameters...]**&#x200B;链接允许您指定下面显示的其他选项：

   ![](assets/download_web_edit_advanced.png)

   **[!UICONTROL Process errors]**&#x200B;选项在[处理错误](monitoring-workflow-execution.md#processing-errors)中有详细说明。

## 输出参数 {#output-parameters}

* 文件名：已下载文件的完整名称。
