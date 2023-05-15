---
product: campaign
title: 开始和结束
description: 了解有关开始和结束工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 56dfbaf3-93de-4ade-b4ad-9b54d239c7a5
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 4%

---

# 开始和结束{#start-and-end}



的 **[!UICONTROL Start]** 和 **[!UICONTROL End]** 活动允许您以图形方式标记工作流的开始和结束。 这些活动对功能没有影响，因此是可选的。

* **[!UICONTROL Start]**

   从没有集客过渡和开始类型活动的活动开始执行工作流。

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   您可以配置 **[!UICONTROL End]** 活动，以中断所有正在进行的任务。 为此，请双击活动以显示其属性，并选中相应的选项。

   ![](assets/s_user_segmentation_end.png)

   启用结束活动后，工作台中的数据会自动删除。 如果不需要执行此操作，并且为了避免不必要的加载，您可以选择在最后一个活动输出时禁用过渡。 例如，在投放输出中，如果没有计划进程，请取消选中相关选项，如下所示：

   ![](assets/s_advuser_delivery_option_no_output.png)
