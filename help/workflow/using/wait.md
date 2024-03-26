---
product: campaign
title: 等待
description: 了解有关等待工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 4%

---

# 等待{#wait}



A **等待** 活动会在延迟几秒到几个月之间的任何时间后激活其过渡。 等待任务不会阻止执行其他任务；当此任务处于挂起状态时，工作流可以并行执行任务。

您可以使用编辑器输入标签和等待时间，如以下示例所示：

![](assets/edit_wait.png)

在 **[!UICONTROL Duration]** 字段中，该值可以以您选择的单位表示：（根据运算符的区域设置）：

* 如果未指定区域设置： **s** 几秒钟， **m** 就几分钟， **h** 数小时， **d** 好几天了， **y** 好几年了。 审批时，该值将自动转换为最易读的单位。

  默认单位是日(**d**)。

* 而，例如，如果区域设置设置为“Français”： **s** 几秒钟， **mn** 就几分钟， **h** 数小时， **j** 好几天了， **m** 好几个月了， **a** 好几年了。 审批时，该值将自动转换为最易读的单位，如上面的示例所示 **90年代** 已转换为 **1mn 30s**.

  默认单位是日(**d**)。
