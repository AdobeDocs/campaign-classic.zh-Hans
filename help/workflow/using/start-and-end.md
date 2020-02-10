---
title: 开始和结束
seo-title: 开始和结束
description: 开始和结束
seo-description: null
page-status-flag: never-activated
uuid: ec0c818c-c307-4f50-908c-507bce0ea27b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 8b239d5e-2317-42c8-9fee-7d40bea624da
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 开始和结束{#start-and-end}

通过 **[!UICONTROL Start]** 和 **[!UICONTROL End]** 活动，您可以以图形方式标记工作流的开始和结束。 这些活动没有功能影响，因此是可选的。

* **[!UICONTROL Start]**

   执行工作流以活动开始，而没有入站过渡和“开始”类型活动。

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   您可以配置活 **[!UICONTROL End]** 动以中断所有正在执行的任务。 为此，请双击活动以显示其属性，然后选中相应的选项。

   ![](assets/s_user_segmentation_end.png)

   启用结束活动后，工作台中的数据会自动删除。 如果这不是必需的，并且要避免不必要的加载，您可以选择在上次活动输出时禁用过渡。 例如，在交付输出中，如果没有预定进程，请取消选中以下相关选项：

   ![](assets/s_advuser_delivery_option_no_output.png)

