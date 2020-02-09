---
title: 重复数据删除
seo-title: 重复数据删除
description: 重复数据删除
seo-description: null
page-status-flag: never-activated
uuid: 90dee589-ac45-442e-89ef-1c14bb22200d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 83b915bd-7e23-41b5-9f9a-f7eb72026376
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 重复数据删除{#deduplication}

重复数据删除会删除入站活动结果中的重复项。 可以在电子邮件地址、电话号码或其他字段上执行重复数据删除。

## 最佳实践 {#best-practices}

在重复数据消除期间，入站流将单独处理。 如果在查询1的结果和查询2的结果中找到实例收件人A，则不会删除重复项。

此问题需要解决：

* 创建 **Union** 活动以统一每个入站流。
* 在Union活 **动之后** ，创建重复数 **据消除活动** 。

![](assets/dedup_bonnepratique.png)

## 配置 {#configuration}

要配置重复数据消除，请输入其标签、方法和重复数据消除标准，以及与结果相关的选项。

单击链 **[!UICONTROL Edit configuration...]** 接以定义重复数据消除模式。

![](assets/s_user_segmentation_dedup_param.png)

1. 目标选择

   选择此活动的目标类型（默认情况下，重复数据消除问题会引起收件人的注意）和要使用的标准，即相同值允许您标识重复项的字段：电子邮件地址、手机或电话号码、传真号码或直邮地址。

   ![](assets/s_user_segmentation_dedup_param2.png)

   在下一步中，通过选 **[!UICONTROL Other]** 项可以选择要使用的标准或标准：

   ![](assets/s_user_segmentation_dedup_param3.png)

1. 重复数据删除方法

   从下拉列表中，选择要使用的重复数据消除方法，并输入要保留的重复项数。

   ![](assets/s_user_segmentation_dedup_param4.png)

   可以使用以下方法：

   * **[!UICONTROL Choose for me]**:随机选择要从副本中保留的记录。
   * **[!UICONTROL Following a list of values]**:允许您为一个或多个字段定义值优先级。 要定义值，请选择字段或创建表达式，然后将值添加到相应的表中。 要定义新字段，请单击 **[!UICONTROL Add]** 值列表上方的按钮。

      ![](assets/s_user_segmentation_dedup_param5.png)

   * **[!UICONTROL Non-empty value]**:这样，您就可以保留选定表达式的值不作为优先级的记录。

      ![](assets/s_user_segmentation_dedup_param6.png)

   * **[!UICONTROL Using an expression]**:允许您使用给定表达式的最低（或最高）值保存记录。

      ![](assets/s_user_segmentation_dedup_param7.png)
   单击 **[!UICONTROL Finish]** 以批准选定的重复数据消除方法。

   窗口的中间部分汇总定义的配置。

   在活动编辑器窗口的下半部分，您可以修改图形对象的出站过渡的标签，并输入将与活动结果关联的区段代码。 此代码稍后可用作定位标准。

   ![](assets/s_user_segmentation_dedup_param8.png)

   如果您 **[!UICONTROL Generate complement]** 希望利用剩余人口，请选中此选项。 补码由所有副本组成。 然后，将向活动添加其他过渡，如下所示：

   ![](assets/s_user_segmentation_dedup_param9.png)

## 示例：在交付前识别重复项 {#example--identify-the-duplicates-before-a-delivery}

在以下示例中，重复数据消除涉及三个查询的联合。

该工作流的目的是通过排除重复项来定义传送目标，以避免多次将其发送给同一收件人。

标识的副本还将集成到专用副本列表中，如有必要，可重复使用。

![](assets/deduplication_example.png)

1. 添加并链接工作流操作所需的各种活动，如上所示。

   此处使用联合活动将三个查询“统一”为一个过渡。 因此，重复数据消除不会单独用于每个查询，而是用于整个查询。 有关此主题的详细信息，请参阅最 [佳实践](#best-practices)。

1. 打开重复数据消除活动，然后单 **[!UICONTROL Edit configuration...]** 击链接以定义重复数据消除模式。
1. 在新窗口中，选择 **[!UICONTROL Database schema]**。
1. 选择“ **收件人** ”作为定位和筛选维。
1. 为重复项选择ID字 **[!UICONTROL Email]** 段，以仅向每个电子邮件地址发送一次传送，然后单击 **[!UICONTROL Next]**。

   如果您希望将重复的ID基于特定字段，请选择以 **[!UICONTROL Other]** 访问可用字段列表。

1. 当为多个收件人标识了同一电子邮件地址时，选择仅保留一个条目。
1. 选择重 **[!UICONTROL Choose for me]** 复数据消除模式，以便随机选择在识别重复的情况下保存的记录，然后单击 **[!UICONTROL Finish]**。

运行工作流时，所有标识为重复项的收件人都将从结果中排除（因此也会从传送中排除）并添加到重复项列表。 此列表可以再次使用，而不必重新标识重复项。

## 输入参数 {#input-parameters}

* tableName
* 架构

每个入站事件都必须指定由这些参数定义的目标。

## 输出参数 {#output-parameters}

* tableName
* 架构
* recCount

这三组值标识了重复数据消除所导致的目标。 **[!UICONTROL tableName]** 是保存目标标识符的表的名称， **[!UICONTROL schema]** 是人群的架构（通常是nms:recipient）, **[!UICONTROL recCount]** 是表中的元素数。

与补码相关联的过渡具有相同的参数。
