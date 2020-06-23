---
title: 数据加载（文件）
description: 进一步了解数据加载（文件）活动。
page-status-flag: never-activated
uuid: c064aa23-412e-49b4-a51d-b0e8ca572f2e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: dcb5b8e8-be38-4d89-908d-f57c2413a9bc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9c9554b83726da7a7dbc747878d7d0758e71a4d7
workflow-type: tm+mt
source-wordcount: '1051'
ht-degree: 0%

---


# 数据加载（文件）{#data-loading-file}

## 使用 {#use}

该 **[!UICONTROL Data loading (File)]** 活动允许您直接访问外部数据源并在Adobe Campaign中使用它。 事实上，定位操作所需的所有数据并不总是在Adobe Campaign库中找到： 可在外部文件中使用。

要加载的文件可由过渡指定或在执行此活动时计算。 例如，它可以是客户端10个最喜爱产品的列表，这些产品的购买在外部数据库中进行管理。

在此活动的配置窗口的上半部分允许您定义文件格式。 为此，请使用与要导入的文件格式相同的示例文件。 此文件可以存储在本地或服务器上。

>[!CAUTION]
>
>仅支持“平面”结构文件（如CSV、TXT等）。 不建议使用XML格式。

![](assets/s_advuser_wf_etl_file.png)

您可以定义在文件导入过程中要执行的预处理，例如，这样不必在服务器上解压文件（因此为解压文件节省空间），而是在文件处理中包含解压。 选择选 **[!UICONTROL Pre-process the file]** 项，然后从3个选项中进行选择： **[!UICONTROL None]**、 **[!UICONTROL Decompression]** (zcat)或 **[!UICONTROL Decrypt]** (gpg)。

![](assets/preprocessing-dataloading.png)

有关此内容的详细信息，请参阅此部分： [在处理之前解压或解密文件](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing)。

## 定义文件格式 {#defining-the-file-format}

加载文件时，将自动检测列格式以及每种数据类型的默认参数。 您可以修改这些默认参数，以指定要应用于数据的特定进程，尤其是当存在错误或空值时。

为此，请 **[!UICONTROL Click here to change the file format...]** 在活动的主窗口中选 **[!UICONTROL Data loading (file)]** 择。 随后将打开格式详细信息窗口。

![](assets/file_loading_columns_format.png)

然后，您可以修改文件的常规格式以及每列的格式。

通用文件格式允许您定义列的识别方式（文件编码、使用分隔符等）。

列格式允许您定义每列的值处理：

* **[!UICONTROL Ignore column]**: 在数据加载过程中不处理此列。
* **[!UICONTROL Data type]**: 指定每列所需的数据类型。
* **[!UICONTROL Allow NULLs]**: 指定如何管理空值。

   * **[!UICONTROL Adobe Campaign default]**: 仅为数字字段生成错误，否则插入NULL值。
   * **[!UICONTROL Empty value allowed]**: 授权空值。 因此插入值NULL。
   * **[!UICONTROL Always populated]**: 如果值为空，则生成错误。

* **[!UICONTROL Length]**: 指定字符串数据类型的最 **大字符** 数。
* **[!UICONTROL Format]**: 定义时间和日期格式。
* **[!UICONTROL Data transformation]**: 定义是否需要对字符串应用字符大小写 **过程**。

   * **[!UICONTROL None]**: 导入的字符串未修改。
   * **[!UICONTROL First letter in upper case]**: 带大写的字符串开始的每个单词的第一个字母。
   * **[!UICONTROL Upper case]**: 字符串中的所有字符均为大写。
   * **[!UICONTROL Lower case]**: 字符串中的所有字符均以小写字母形式显示。

* **[!UICONTROL White space management]**: 指定字符串中是否需要忽略某些空格。 值 **[!UICONTROL Ignore spaces]** 只允许忽略字符串开头和结尾的空格。
* **[!UICONTROL Error processings]**: 定义遇到错误时的行为。

   * **[!UICONTROL Ignore the value]**: 将忽略该值。 工作流执行日志中会生成警告。
   * **[!UICONTROL Reject line]**: 不处理整行。
   * **[!UICONTROL Use a default value in case of error]**: 将导致错误的值替换为在字段中定义的默认值 **[!UICONTROL Default value]** 。
   * **[!UICONTROL Reject the line when there is no remapping value]**: 除非为错误值定义了映射，否则不会处理整行(请参阅 **[!UICONTROL Mapping]** 下面的选项)。
   * **[!UICONTROL Use a default value in case the value is not remapped]**: 将导致错误的值替换为默认值(在字段中定 **[!UICONTROL Default value]** 义)，除非为错误值定义了映射(请参 **[!UICONTROL Mapping]** 阅下面的选项)。

* **[!UICONTROL Default value]**: 根据所选的错误处理指定默认值。
* **[!UICONTROL Mapping]**: 此字段仅在列详细信息配置中可用(通过多次单击或列列表右侧的选项访问)。 导入某些值时，这会转换这些值。 例如，您可以将“three”转换为“3”。

## 示例： 收集数据并将其加载到数据库中 {#example--collecting-data-and-loading-it-in-the-database}

以下示例允许您每天在服务器上收集文件、加载其内容并根据其包含的信息更新数据库中的数据。 要收集的文件包含客户的信息，这些客户可能已购买（价格在3000欧元以上）、要求购买时退款，或者在没有购买任何商品的情况下访问商店。 根据此信息，各种进程将应用于其用户档案库中的进程。

![](assets/s_advuser_load_file_sample_0.png)

1. 通过文件收集器可以恢复存储在目录中的文件，具体取决于给定的频率。

   该选 **[!UICONTROL Directory]** 项卡包含有关要恢复的文件的信息。 在我们的示例中，将恢复名称包含单词“customers”且存储在服务器tmp/Adobe/Data/files目录中的所有文本格式的文件。

   使用方 **[!UICONTROL File collector]** 式详见“ [文件收集器](../../workflow/using/file-collector.md) ”部分。

   ![](assets/s_advuser_load_file_sample_1.png)

   通过 **[!UICONTROL Schedule]** 该选项卡可以计划收集器的执行，即指定检查这些文件存在的频率。

   这里，我们希望在每个工作日晚上9点触发收集器。

   ![](assets/s_advuser_load_file_sample_2.png)

   为此，请单击 **[!UICONTROL Change...]** 编辑工具右下方的按钮并配置计划。

   For more on this, refer to [Scheduler](../../workflow/using/scheduler.md).

1. 然后，配置数据加载（文件）活动以指示如何读取所收集的文件。 为此，请选择一个与要加载的文件结构相同的示例文件。

   ![](assets/s_advuser_load_file_sample_3.png)

   此处，文件包含五列：

   * 第一列包含与事件一致的代码： 购买（大于或小于3,000欧元），不购买或退款一次或多次购买。
   * 以下四列包含客户端的名字、姓氏、电子邮件和帐号。
   要加载的文件的格式配置与在Adobe Campaign中导入数据时定义的格式配置一致。 For more on this, refer to this [section](../../platform/using/importing-data.md#step-2---source-file-selection).

1. 在拆分活动中，根据事件列值指定要创建的 **子集** 。

   “拆分”活动在一节中详细介绍。

   ![](assets/s_advuser_load_file_sample_4.png)

   对于每个子集，在“事件”列中指定 **一个** 值。

   ![](assets/s_advuser_load_file_sample_5.png)

   因 **[!UICONTROL Split]** 此活动将包含以下信息：

   ![](assets/s_advuser_load_file_sample_6.png)

1. 然后，指定要针对每种类型的人群执行的流程。 在我们的例子中，我们将 **[!UICONTROL Update the data]** 在数据库中。 为此，将活动放 **[!UICONTROL Update data]** 置在拆分活动的每个出站过渡的末尾。

   活动 **[!UICONTROL Update data]** 在“更新数据” [部分中详细](../../workflow/using/update-data.md) 。

