---
product: campaign
title: 定义最终投放
description: 了解如何通过专用用例执行A/B测试
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: A/B Testing
role: User
exl-id: bc23a444-a872-48fb-8bba-64b301541089
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 5%

---

# AB测试：定义最终投放 {#step-6--defining-the-final-delivery}

创建脚本以选择A/B测试入选者后，您可以定义最终投放的参数。

1. 连接 **[!UICONTROL JavaScript code]** 活动到剩余 **[!UICONTROL Delivery]** 活动。
1. 打开 **[!UICONTROL Delivery]** 活动。
1. 取消选中 **[!UICONTROL Generate an outbound transition]** 选项完成此活动的工作流。
1. 将其他选项保留为其默认值。

   ![](assets/ab_test_final_delivery.png)

通过准备过渡中指定的投放(通过 **[!UICONTROL Javascript Code]** 然后，您可以批准它并开始发送，如下一步骤中所述。

您现在可以启动工作流。 [了解详情](a-b-testing-uc-start-workflow.md)。
