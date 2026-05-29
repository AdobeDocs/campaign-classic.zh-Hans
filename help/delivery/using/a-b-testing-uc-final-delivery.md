---
product: campaign
title: 定义最终投放
description: 了解如何通过专用用例执行A/B测试
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: A/B Testing
role: User
exl-id: bc23a444-a872-48fb-8bba-64b301541089
TQID: https://experienceleague.adobe.com/P0oI4PhLZB-iBFDrEJ2Qy7eIOPYWSWYu5s6j3yCN6j0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
subfeature_v2:
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
  - id: e739ee2b-6228-412e-878f-45de0791417d
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 119
ht-degree: 5%

---

# AB测试：定义最终投放 {#step-6--defining-the-final-delivery}

创建脚本以选择A/B测试入选者后，您可以定义最终投放的参数。

1. 将&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动连接到其余&#x200B;**[!UICONTROL Delivery]**&#x200B;活动。
1. 打开&#x200B;**[!UICONTROL Delivery]**&#x200B;活动。
1. 取消选中&#x200B;**[!UICONTROL Generate an outbound transition]**&#x200B;选项以完成此活动的工作流。
1. 将其他选项保留为其默认值。

   ![](assets/ab_test_final_delivery.png)

通过准备在过渡中指定的投放（通过&#x200B;**[!UICONTROL Javascript Code]**&#x200B;活动定义），您将能够批准该投放并开始发送，如下一步骤中所述。

您现在可以启动工作流。 [了解详情](a-b-testing-uc-start-workflow.md)。
