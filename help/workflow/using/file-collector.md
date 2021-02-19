---
solution: Campaign Classic
product: campaign
title: 文件收集器
description: 进一步了解文件收集器工作流活动
audience: workflow
content-type: reference
topic-tags: event-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# 文件收集器{#file-collector}

**文件收集器**&#x200B;监视一个或多个文件到达一个目录，并对收到的每个文件激活其过渡。 对于每个事件,**[!UICONTROL filename]**&#x200B;变量包含收到的文件的全名。 收集的文件将移至另一个目录以进行归档，并确保只计数一次。

默认情况下，文件收集器是一个持续性任务，在计划指定的时间测试文件是否存在。

文件必须位于执行此工作流的wfserver模块所在的服务器上。 如果在单个实例上部署了多个wfserver模块，则必须指定使用这些文件的活动的关联或工作流的整体关联。

## 属性 {#properties}

**[!UICONTROL File collector]**&#x200B;活动的第一个选项卡允许您选择源目录，并根据需要过滤收集的文件。 其他选项卡详见[入站电子邮件](../../workflow/using/inbound-emails.md)（**[!UICONTROL Schedule]**&#x200B;和&#x200B;**[!UICONTROL Expiry]**&#x200B;选项卡）。

![](assets/file_collect_edit.png)

1. **下载文件**

   * **[!UICONTROL Directory]**

      包含要下载的文件的目录。 必须事先在服务器上创建此目录：如果不存在，将引发错误。

   * **[!UICONTROL Filter]**

      只考虑与此过滤器匹配的文件。 目录中的其他文件将被忽略。 如果筛选器为空，则将考虑目录中的所有文件。 过滤器示例：***.zip**, **import-*.txt**。

   * **[!UICONTROL Stop as soon as a file has been processed]**

      如果启用此选项，则任务在接收到第一个文件后结束。 如果目录中存在与筛选器对应的多个文件，则只会考虑一个文件。 此选项保证只发送一个事件。 文件是列表中按字母顺序排列的第一个文件。

      对于未调度的活动，如果在指定的目录中找不到与过滤器匹配的文件，并且未启用&#x200B;**[!UICONTROL Process file nonexistence]**&#x200B;选项，则会引发错误。

   * **[!UICONTROL Execution schedule]**

      通过&#x200B;**[!UICONTROL Schedule]**&#x200B;选项卡的参数确定文件存在检查的频率。

1. **错误处理**

   以下两个选项可用：

   * **[!UICONTROL Process file nonexistence]**

      每次在指定目录中找不到与筛选器匹配的文件时，此选项都会启动一个特殊过渡。

      如果任务未计划，则此过渡将仅激活一次。

   * **[!UICONTROL Processing errors]**

      此选项使出现特殊过渡，以在生成错误时激活。 在这种情况下，工作流不会更改为错误状态，并继续执行

      考虑到的错误是文件系统错误（无法移动文件、无法访问目录等）。

      此选项不处理与活动配置相关的错误，即无效值。

1. **历史化**

   请参阅此处的&#x200B;**[!UICONTROL File historization]**&#x200B;步骤：[Web下载](../../workflow/using/web-download.md)。

无法确定文件处理顺序。 要按顺序处理一组文件，请使用&#x200B;**[!UICONTROL Stop as soon as a file has been processed]**&#x200B;选项并创建一个循环。 在这种情况下，将按字母顺序处理文件。 使用&#x200B;**[!UICONTROL Process file nonexistence]**&#x200B;选项可以完成小版本。

![](assets/file_collect_loop.png)

## 输出参数{#output-parameters}

* 文件名：完整文件名。 这是将文件名移到历史化目录后的文件名。 因此，路径不同，但如果目录中已存在同名的其他文件，则名称也不同。 延长保留。
