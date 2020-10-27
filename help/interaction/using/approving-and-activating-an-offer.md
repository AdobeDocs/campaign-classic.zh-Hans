---
title: 批准和激活优惠
seo-title: 批准和激活优惠
description: 批准和激活优惠
seo-description: null
page-status-flag: never-activated
uuid: 1be96bb4-ef17-4b4d-b872-05e1c6b1412d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: 7b1c58a0-6fd6-4c9d-b1c4-f3dffda42523
translation-type: tm+mt
source-git-commit: 8fc3e793ec544948049fc122b44b6bffdebecba0
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 3%

---


# 批准和激活优惠{#approving-and-activating-an-offer}

优惠内容完成后，您需要批准它，以便将其复制到实时环境并交付。 批准涉及优惠内容及其资格。

优惠仪表板上的横幅告诉您优惠是否需要完成审批周期。

![](assets/offer_validate_001.png)

## 批准优惠内容 {#approving-offer-content}

批准优惠内容意味着选择要在实时环境中提供的表示形式。

优惠的内容具有每个空格的一个表示形式。 由于每个优惠空间都有其自己的结构和自己的渲染功能，因此优惠呈现可能会有所不同。

您可以选择批准某些可用空间上的优惠内容，而拒绝其他空间上的内容。

>[!IMPORTANT]
>
>优惠的内容和资格获得批准后，发布工作流(优惠通知)将自动运行，优惠将实时显示并在所有激活的空间上可用。

要批准优惠内容，请应用以下步骤：

1. 单击按 **[!UICONTROL Approval]** 钮并在弹 **[!UICONTROL Approve content]** 出窗口中选择。

   ![](assets/offer_validate_002.png)

1. 使用下拉列表，选择要继续编辑的表示或要发布到实时环境的表示，然后单击 **[!UICONTROL Content approval]**。

   ![](assets/offer_validate_003.png)

   优惠内容获得批准后，优惠仪表板表上的信息将更新。

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >提 **[!UICONTROL Content approved]** 及并不意味着所有优惠呈现均已启用和批准。 它表示内容批准流程已完成，无论是否已启用／批准所有优惠。

## 批准优惠资格 {#approving-offer-eligibility}

批准优惠资格是指接受或拒绝优惠权重，并且合格规则也在优惠中配置或继承在父类别中创建的规则。

>[!IMPORTANT]
>
>优惠的内容和资格获得批准后，发布工作流(优惠通知)将自动运行，优惠将实时显示并在所有激活的空间上可用。

* 可通过单击查看规则的完整列表 **[!UICONTROL Schedule and eligibility rules]**。

   ![](assets/offer_validate_005.png)

* 要更改合格规则，请单 **[!UICONTROL Reject]**&#x200B;击，然后单击 **[!UICONTROL Eligibility approval]**。

   ![](assets/offer_validate_007.png)

   各个状态会在优惠仪表板中更新。

   ![](assets/offer_validate_006.png)

* 要接受优惠资格，请单击 **[!UICONTROL Approve eligibility]**。

   ![](assets/offer_validate_008.png)

   批准资格，根据需要添加评论，然后单击 **[!UICONTROL Eligibility approval]**。

   ![](assets/offer_validate_009.png)

   各个状态会在优惠仪表板中更新。

   ![](assets/offer_validate_010.png)

## 批准跟踪 {#approval-tracking}

批准跟踪可用于优惠仪表板。 单击 **[!UICONTROL Hide/display logs]** 即可访问它。

![](assets/offer_validate_012.png)

>[!NOTE]
>
>优惠的选项卡中也 **[!UICONTROL Audit]** 提供跟踪功能，其中包含审阅者注释的详细信息。

## 重新开始批准 {#restart-the-approval}

一旦启动批准，即可重新启动。 为此，请按照以下说明操作：

1. 单击 **[!UICONTROL Content approved]** 优惠仪表板。
1. 在显示 **[!UICONTROL Edit]** 的窗口中，选择要重新启动的批准，然后单击 **[!UICONTROL Re-initialize approval to submit it again]**。
1. 单击进行确 **[!UICONTROL Ok]**&#x200B;认。

![](assets/offer_validate_013.png)

## 发布优惠 {#publishing-the-offer}

优惠的内容和资格一经批准，优惠便由一个工作流发布，该工作流将自动为其批准周期已结束的每个优惠运行。 该工 **[!UICONTROL Offer notification]** 作流还每小时运行一次，以便将优惠目录中包含的空格和类别从设计环境同步到实时环境。

设计环境中可用仪表板的优惠包含有关发布的信息，包括实时环境中匹配优惠的名称。

![](assets/offer_golive_001.png)

要显示实时优惠中可用的环境，请单击优惠标签：实时优惠具有包含其所有相关信息的仪表板。

![](assets/offer_golive_002.png)

## 禁用优惠 {#disabling-an-offer}

优惠获得批准后，您可以禁用它。

为此，请转到仪表板，查找在线优惠或等待上线的优惠，然后单击 **[!UICONTROL Disable offer]**。

您还可以通过转到选项卡并选中框 **[!UICONTROL Eligibility]** 来直接禁用类别 **[!UICONTROL Enabled]** 。

>[!NOTE]
>
>在设计优惠中删除某个环境后，该环境会在链接的在线中自动取消激活。 在提议保留期后，取消激活的优惠从在线环境中删除。

![](assets/offer_preview_deactivate.png)

