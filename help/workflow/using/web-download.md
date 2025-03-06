---
product: campaign
title: Web 下载
description: 了解有关Web下载工作流活动的更多信息
feature: Workflows
hide: true
hidefromtoc: true
exl-id: b6005eae-5fbc-4e22-ab3a-c9b7ed6506f6
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 2%

---

# Web 下载{#web-download}



**Web下载**&#x200B;活动启动文件下载，下载对象为显式URL、外部帐户或Adobe Campaign实例。 使用HTTP协议。 这可以是GET或POST下载。

## 属性 {#properties}

1. **选择Web文件**

   要指定要下载的文件，您可以输入文件URL，使用存储文件的外部HTTP帐户，或通过Adobe Campaign实例加载文件。 可用参数详述如下：

   * 要直接输入要下载的文件的URL，请选择&#x200B;**[!UICONTROL Explicit URL]**&#x200B;选项，并在相应的字段中指定URL。 此URL可使用变量数据构建。

     ![](assets/download_web_edit.png)

   * 要使用&#x200B;**[!UICONTROL External account]**，请从下拉列表中选择帐户，并指定要下载的文件。

     从Adobe Campaign树的&#x200B;**[!UICONTROL Administration > Platform > External accounts]**&#x200B;节点配置外部帐户。 可通过&#x200B;**[!UICONTROL Edit link]**&#x200B;图标编辑帐户参数。

     ![](assets/download_web_edit_external.png)

   * 要从Adobe Campaign实例下载文件，请选择&#x200B;**[!UICONTROL Adobe Campaign Instance]**&#x200B;选项。

     ![](assets/download_web_edit_instance.png)

1. **文件历史化**

   **[!UICONTROL File historization settings...]**&#x200B;链接允许您指定文件存储目录和此目录的清除频率。

   ![](assets/download_web_edit_hist.png)

   可以使用以下选项：

   * **[!UICONTROL Use a default storage directory]**：始终在处理之前移动文件。 如果选中此选项，则文件将移至默认存储目录(Adobe Campaign安装文件夹的&#x200B;**vars**&#x200B;目录)中。 要指定存储目录，请取消选中该框并在&#x200B;**[!UICONTROL Storage directory]**&#x200B;字段中输入其路径
   * **[!UICONTROL Number of files]**：输入存储目录中要保留的最大文件数。
   * **[!UICONTROL Maximum size (in Mb)]**：输入存储目录的最大容量（以MB为单位）。

   每个文件在遵守规定的清除规则之前保留24小时。 清除操作在活动开始之前进行，因此不考虑正在进行的工作流文件。

   文件会根据其存在时间（从最旧到最新）进行删除。 最早的文件将被清除，直到两个清除规则都得到验证为止。 因此，如果定义了100个文件的限制，则意味着存储目录将始终包含工作流开始前的100个最新文件，以及正在进行的工作流中正在处理的文件。

   如果您不再希望为&#x200B;**[!UICONTROL Number of files]**&#x200B;和&#x200B;**[!UICONTROL Maximum size (in Mb)]**&#x200B;选项设置限制，请输入0作为值。

1. **高级参数**

   **[!UICONTROL Advanced parameters...]**&#x200B;链接允许您指定下面显示的其他选项：

   * **[!UICONTROL Follow redirections]**：文件重定向允许您使用覆盖将数据输入或输出定向到其他类型的设备。
   * **[!UICONTROL Add the HTTP headers to the file]**：在某些情况下，您可能希望向文件添加其他HTTP标头。 最常见的是，这些标头将用于提供其他信息以进行故障排除，用于[跨源资源共享(CORS)](https://developer.mozilla.org/docs/Web/HTTP/CORS)，或用于设置特定的缓存指令。
   * **[!UICONTROL Ignore the HTTP return code]**： HTTP返回代码（也称为HTTP状态代码）表示HTTP请求的结果。

   ![](assets/download_web_edit_advanced.png)

   **[!UICONTROL Process errors]**&#x200B;选项在[处理错误](monitoring-workflow-execution.md#processing-errors)中有详细说明。

## 输出参数 {#output-parameters}

* 文件名：下载文件的完整名称。
