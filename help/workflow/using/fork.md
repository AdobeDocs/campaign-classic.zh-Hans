---
product: campaign
title: 分叉
description: 了解有关分支工作流活动的更多信息
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 3%

---

# 分叉{#fork}



您可以使用 **[!UICONTROL Fork]** 活动，以创建多个叫客过渡，并在同一工作流中独立运行多个活动。

>[!IMPORTANT]
>
>您在之后添加的叫客过渡 **[!UICONTROL Fork]** 活动不会同时运行。 此行为可能会影响工作流性能。 使用 **[!UICONTROL Fork]** 活动。 （可选）您可以在工作流的后续部分之前加入叫客活动。

配置 **[!UICONTROL Fork]** 活动及其相关活动，请执行以下步骤：

1. 打开 **[!UICONTROL Fork]** 活动，并定义叫客过渡的名称和标签。

   ![](assets/s_user_segmentation_fork.png)

1. 打开每个叫客过渡并进行配置。
1. （可选）要加入叫客过渡，请添加AND加入活动。 [了解详情](and-join.md)。

   工作流的后续部分仅在联接的叫客过渡完成后运行。

## 示例：分段

在本例中，不同的电子邮件被发送到不同的群体。 A **[!UICONTROL Fork]** 活动在查询之后使用，以并行执行两个操作：

* 保存查询结果
* 对发送多个投放的结果进行分段

  ![分支活动位于两个查询的交叉点之后，位于列表更新活动和拆分活动之前。](assets/wkf_fork_example.png)

工作流包含以下活动：

1. **[!UICONTROL Query]** 活动

   选定了两个人口群体：妇女和巴黎人。

1. **[!UICONTROL Intersection]** 活动

   查询结果的交集（即巴黎女性）被选中。

1. **[!UICONTROL Fork]** 活动

   这将保存计算出的群体，并会同时将其分为两组：

   1. 18至40岁的巴黎妇女
   1. 40岁以上的巴黎妇女

1. **[!UICONTROL Delivery]** 活动

   向每个群体组发送不同的电子邮件。

## 用例：发送生日电子邮件

定期电子邮件会在收件人的生日当天发送给收件人列表。 A **[!UICONTROL Fork]** 活动用于包含闰年2月29日出生的收件人。 [了解详情](sending-a-birthday-email.md) 关于此用例。

![分支活动位于测试活动之后，且位于两个查询活动之前。](assets/birthday-workflow_usecase_1.png)

## 用例：通过工作流自动提供内容

内容块的创建和投放实现了自动化。 A **[!UICONTROL Fork]** 活动用于计算目标，并同时用于创建内容。 [了解详情](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) 关于此用例。

![分支活动紧跟在投放活动之后，位于查询活动和内容管理活动之前，这两个活动均通过AND-join活动连接。](../../delivery/using/assets/d_ncs_content_workflow10.png)

然后，您可以配置每个叫客过渡，然后使用将它们联接在一起 [AND — 连接](and-join.md) 活动（如果需要）。 这样，工作流的其余部分将只在 **[!UICONTROL Fork]** 活动的叫客过渡已完成。

## 相关主题

* [AND-join 活动](and-join.md)
* [用例：生日电子邮件](sending-a-birthday-email.md)
* [用例：内容创建和交付](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)