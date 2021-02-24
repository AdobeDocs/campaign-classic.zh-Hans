---
solution: Campaign Classic
product: campaign
title: 定义最终投放
description: 了解如何通过专用的用例执行A/B测试。
audience: delivery
content-type: reference
topic-tags: a-b-testing
translation-type: tm+mt
source-git-commit: 50a10e16f320a67cb4ad0e31c1cbe8a9365b7887
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---


# 定义最终投放{#step-6--defining-the-final-delivery}

创建脚本以选择A/B测试入选方后，您可以定义最终投放的参数。

1. 将&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动连接到其余&#x200B;**[!UICONTROL Delivery]**&#x200B;活动。
1. 打开&#x200B;**[!UICONTROL Delivery]**&#x200B;活动。
1. 取消选中&#x200B;**[!UICONTROL Generate an outbound transition]**&#x200B;选项，以使用此活动完成工作流。
1. 将其他选项保留为其默认值。

   ![](assets/ab_test_final_delivery.png)

通过准备在过渡中指定的投放(通过&#x200B;**[!UICONTROL Javascript Code]**&#x200B;活动定义)，您随后可以批准该并开始发送，如下一步所述。

您现在可以开始工作流(请参阅[步骤7:开始工作流](../../delivery/using/a-b-testing-uc-start-workflow.md))。
