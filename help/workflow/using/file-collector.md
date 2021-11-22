---
product: campaign
title: 文件收集器
description: 了解有关文件收集器工作流活动的更多信息
audience: workflow
content-type: reference
topic-tags: event-activities
exl-id: bbec389e-c2ba-4b23-847f-b01dca6b8d5a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# 文件收集器{#file-collector}

![](../../assets/common.svg)

的 **文件收集器** 监视一个或多个文件到达目录中的情况，并为收到的每个文件激活其过渡。 对于每个事件， **[!UICONTROL filename]** 变量包含收到的文件的全名。 收集的文件将移至其他目录以进行存档，并确保只计数一次。

默认情况下，文件收集器是一项永久性任务，用于在计划指定的时间测试文件的存在。

文件必须位于负责此工作流的wfserver模块所在的服务器上。 如果在单个实例上部署了多个wfserver模块，则必须指定使用这些文件的活动的关联或工作流的整体关联。

## 属性 {#properties}

的第一个选项卡 **[!UICONTROL File collector]** 活动允许您选择源目录，并根据需要筛选收集的文件。 其他选项卡在 [入站电子邮件](inbound-emails.md) (**[!UICONTROL Schedule]** 和 **[!UICONTROL Expiry]** 选项卡)。

![](assets/file_collect_edit.png)

1. **下载文件**

   * **[!UICONTROL Directory]**

      包含要下载的文件的目录。 此目录必须事先在服务器上创建：如果不存在，则会引发错误。

   * **[!UICONTROL Filter]**

      只考虑与此过滤器匹配的文件。 目录中的其他文件将被忽略。 如果筛选器为空，则将考虑目录中的所有文件。 过滤器示例： ***.zip**, **import-*.txt**.

   * **[!UICONTROL Stop as soon as a file has been processed]**

      如果启用此选项，则任务将在收到第一个文件后结束。 如果目录中存在与过滤器对应的多个文件，则只会考虑一个文件。 此选项可保证仅发送一个事件。 需要考虑的文件是列表中按字母顺序排列的第一个文件。

      对于未计划的活动，如果在指定的目录中未找到与筛选器匹配的文件，以及 **[!UICONTROL Process file nonexistence]** 选项时，将引发错误。

   * **[!UICONTROL Execution schedule]**

      通过 **[!UICONTROL Schedule]** 选项卡。

1. **错误处理**

   以下两个选项可供使用：

   * **[!UICONTROL Process file nonexistence]**

      每当在指定目录中未找到与筛选器匹配的文件时，此选项将启动一个特殊过渡。

      如果未计划任务，则此过渡将仅激活一次。

   * **[!UICONTROL Processing errors]**

      此选项会显示一个特殊过渡，在生成错误时激活。 在这种情况下，工作流不会更改为错误状态，并继续执行

      需考虑的错误是文件系统错误（无法移动文件、无法访问目录等）。

      此选项不处理与活动配置相关的错误，即无效值。

1. **历史化**

   请参阅 **[!UICONTROL File historization]** 步骤： [Web下载](web-download.md).

无法确定文件处理顺序。 要按顺序处理一组文件，请使用 **[!UICONTROL Stop as soon as a file has been processed]** ，并创建循环。 在这种情况下，将按字母顺序处理文件。 的 **[!UICONTROL Process file nonexistence]** 选项可让您完成迭代。

![](assets/file_collect_loop.png)

## 输出参数 {#output-parameters}

* 文件名：完整文件名。 这是文件被移动到历史化目录后的文件名。 因此，路径不同，但如果目录中已存在同名的其他文件，则名称也不同。 保留扩展。
