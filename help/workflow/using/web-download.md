---
product: campaign
title: Web 下载
description: 了解有关Web下载工作流活动的更多信息
feature: Workflows
exl-id: b6005eae-5fbc-4e22-ab3a-c9b7ed6506f6
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 2%

---

# Web 下载{#web-download}



此 **Web下载** 活动可启动文件下载，下载对象可以是显式URL、外部帐户或Adobe Campaign实例。 使用HTTP协议。 这可以是GET或POST下载。

## 属性 {#properties}

1. **选择Web文件**

   要指定要下载的文件，您可以输入文件URL，使用存储文件的外部HTTP帐户，或通过Adobe Campaign实例加载文件。 可用参数详述如下：

   * 要直接输入要下载的文件的URL，请选择 **[!UICONTROL Explicit URL]** 选项，并在相应的字段中指定URL。 此URL可使用变量数据构建。

     ![](assets/download_web_edit.png)

   * 要使用 **[!UICONTROL External account]**，从下拉列表中选择帐户，并指定要下载的文件。

     外部帐户是从 **[!UICONTROL Administration > Platform > External accounts]** Adobe Campaign树的节点。 可以通过以下方式编辑帐户参数 **[!UICONTROL Edit link]** 图标。

     ![](assets/download_web_edit_external.png)

   * 要从Adobe Campaign实例下载文件，请选择 **[!UICONTROL Adobe Campaign Instance]** 选项。

     ![](assets/download_web_edit_instance.png)

1. **文件历史化**

   此 **[!UICONTROL File historization settings...]** 链接用于指定文件存储目录和此目录的清除频率。

   ![](assets/download_web_edit_hist.png)

   可以使用以下选项：

   * **[!UICONTROL Use a default storage directory]**：始终先移动文件，然后再进行处理。 如果选中此选项，则文件将移至默认存储目录( **变量** Adobe Campaign目录)。 要指定存储目录，请取消选中复选框，然后在 **[!UICONTROL Storage directory]** 字段
   * **[!UICONTROL Number of files]**：输入存储目录中要保留的最大文件数。
   * **[!UICONTROL Maximum size (in Mb)]**：输入存储目录的最大容量（以MB为单位）。

   每个文件在遵守规定的清除规则之前保留24小时。 清除操作在活动开始之前进行，因此不考虑正在进行的工作流文件。

   文件会根据其存在时间（从最旧到最新）进行删除。 最早的文件将被清除，直到两个清除规则都得到验证为止。 因此，如果定义了100个文件的限制，则意味着存储目录将始终包含工作流开始前的100个最新文件，以及正在进行的工作流中正在处理的文件。

   如果您不想再为 **[!UICONTROL Number of files]** 和 **[!UICONTROL Maximum size (in Mb)]** 选项，请输入0作为值。

1. **高级参数**

   此 **[!UICONTROL Advanced parameters...]** 链接允许您指定下面显示的其他选项：

   ![](assets/download_web_edit_advanced.png)

   此 **[!UICONTROL Process errors]** 有关选项的详情，请参阅 [正在处理错误](monitoring-workflow-execution.md#processing-errors).

## 输出参数 {#output-parameters}

* 文件名：下载文件的完整名称。
