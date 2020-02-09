---
title: 文件收集器
seo-title: 文件收集器
description: 文件收集器
seo-description: null
page-status-flag: never-activated
uuid: 57ef7b2b-f257-4d76-970f-55aece719cec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: event-activities
discoiquuid: 9b937d4d-55ae-4bd4-8dc6-eea42f15b69f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 文件收集器{#file-collector}

“文 **件”(File** )收集器监视目录中一个或多个文件的到达情况，并为收到的每个文件激活其过渡。 对于每个事件， **[!UICONTROL filename]** 变量都包含收到的文件的完整名称。 收集的文件将移至另一个目录以进行存档，并确保仅将其计数一次。

默认情况下，文件收集器是一个永久任务，在计划指定的时间测试文件是否存在。

文件必须位于执行此工作流的wfserver模块所在的服务器上。 如果在单个实例上部署了多个wfserver模块，则必须指定使用这些文件的活动的关联或工作流的整体关联。

## 属性 {#properties}

通过活动的第一个选 **[!UICONTROL File collector]** 项卡，您可以选择源目录，并根据需要过滤收集的文件。 其他选项卡详见入站 [电子邮件](../../workflow/using/inbound-emails.md) (**[!UICONTROL Schedule]** 和选项卡 **[!UICONTROL Expiry]** )。

![](assets/file_collect_edit.png)

1. **下载文件**

   * **[!UICONTROL Directory]**

      包含要下载的文件的目录。 必须事先在服务器上创建此目录：如果它不存在，则会引发错误。

   * **[!UICONTROL Filter]**

      只考虑与此过滤器匹配的文件。 目录中的其他文件将被忽略。 如果过滤器为空，则将考虑目录中的所有文件。 筛选示例： ***.zip**, **import-*.txt**。

   * **[!UICONTROL Stop as soon as a file has been processed]**

      如果启用此选项，则任务在收到第一个文件后结束。 如果目录中存在与过滤器对应的多个文件，则只会考虑一个文件。 此选项可保证仅发送一个事件。 在列表中，考虑的文件是按字母顺序排列的第一个文件。

      对于未调度的活动，如果在指定目录中找不到与过滤器匹配的文件，并且如果未启 **[!UICONTROL Process file nonexistence]** 用该选项，则会引发错误。

   * **[!UICONTROL Execution schedule]**

      通过选项卡的参数确定文件状态检查的频 **[!UICONTROL Schedule]** 率。

1. **错误处理**

   以下两个选项可用：

   * **[!UICONTROL Process file nonexistence]**

      每次在指定的目录中找不到与过滤器匹配的文件时，此选项都会启动一个特殊的过渡。

      如果未计划任务，则此过渡将仅激活一次。

   * **[!UICONTROL Processing errors]**

      此选项会显示一个特殊的过渡，在生成错误时激活。 在这种情况下，工作流不会更改为错误状态，并继续执行

      考虑到的错误是文件系统错误（无法移动文件、无法访问目录等）。

      此选项不处理与活动配置相关的错误，即无效值。

1. **历史化**

   请参阅此 **[!UICONTROL File historization]** 处的步骤：Web [下载](../../workflow/using/web-download.md)。

无法确定文件处理顺序。 要按顺序处理一组文件，请使用该 **[!UICONTROL Stop as soon as a file has been processed]** 选项并创建一个循环。 在这种情况下，将按字母顺序处理文件。 通过 **[!UICONTROL Process file nonexistence]** 此选项可完成小版本。

![](assets/file_collect_loop.png)

## 输出参数 {#output-parameters}

* 文件名

完整文件名。 这是将文件名移到历史记录目录后的文件名。 因此，路径不同，但如果目录中已存在同名的其他文件，则名称也不同。 保留延长。
