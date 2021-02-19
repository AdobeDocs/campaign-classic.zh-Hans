---
solution: Campaign Classic
product: campaign
title: 批准和激活优惠
description: 批准和激活优惠
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 2%

---


# 批准和激活优惠{#approving-and-activating-an-offer}

优惠内容完成后，您需要批准它，以将其复制到实时环境并交付。 批准涉及优惠内容及其资格。

优惠仪表板上的横幅告诉您优惠是否需要完成审批周期。

![](assets/offer_validate_001.png)

## 批准优惠内容{#approving-offer-content}

批准优惠内容意味着选择要在实时环境中提供的表示形式。

优惠的内容具有每个空间的一个表示形式。 由于每个优惠空间都有其自己的结构和自己的渲染功能，因此优惠呈现可能会有所不同。

您可以选择批准某些可用空间上的优惠内容，而拒绝其他空间上的内容。

>[!IMPORTANT]
>
>优惠的内容和资格获得批准后，出版物工作流(优惠通知)将自动运行，优惠将在所有激活的空间上处于活动状态并可用。

要批准优惠内容，请应用以下步骤：

1. 单击&#x200B;**[!UICONTROL Approval]**&#x200B;按钮并在弹出窗口中选择&#x200B;**[!UICONTROL Approve content]**。

   ![](assets/offer_validate_002.png)

1. 使用下拉列表，选择要继续编辑的表示或要发布到实时环境的表示，然后单击&#x200B;**[!UICONTROL Content approval]**。

   ![](assets/offer_validate_003.png)

   优惠内容获得批准后，优惠仪表板表上的信息将更新。

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >**[!UICONTROL Content approved]**&#x200B;提及并不意味着所有优惠呈现都已启用和批准。 它表示内容批准过程已经完成，无论是否已启用/批准所有优惠。

## 批准优惠资格{#approving-offer-eligibility}

批准优惠资格是指接受或拒绝优惠权重，以及在优惠中配置或从父类别中创建的规则继承的合格规则。

>[!IMPORTANT]
>
>优惠的内容和资格获得批准后，出版物工作流(优惠通知)将自动运行，优惠将在所有激活的空间上处于活动状态并可用。

* 可通过单击&#x200B;**[!UICONTROL Schedule and eligibility rules]**&#x200B;查看规则的完整列表。

   ![](assets/offer_validate_005.png)

* 要更改合格规则，请单击&#x200B;**[!UICONTROL Reject]**，然后单击&#x200B;**[!UICONTROL Eligibility approval]**。

   ![](assets/offer_validate_007.png)

   各种状态将在优惠仪表板上更新。

   ![](assets/offer_validate_006.png)

* 要接受优惠资格，请单击&#x200B;**[!UICONTROL Approve eligibility]**。

   ![](assets/offer_validate_008.png)

   批准资格，根据需要添加评论，然后单击&#x200B;**[!UICONTROL Eligibility approval]**。

   ![](assets/offer_validate_009.png)

   各种状态将在优惠仪表板上更新。

   ![](assets/offer_validate_010.png)

## 批准跟踪{#approval-tracking}

批准跟踪可在优惠仪表板中使用。 单击&#x200B;**[!UICONTROL Hide/display logs]**&#x200B;以访问它。

![](assets/offer_validate_012.png)

>[!NOTE]
>
>该优惠的&#x200B;**[!UICONTROL Audit]**&#x200B;选项卡中也提供跟踪功能，其中包含审阅者注释的详细信息。

## 重新启动批准{#restart-the-approval}

一旦启动批准，即可重新启动。 为此，请按照以下说明操作：

1. 单击优惠仪表板上的&#x200B;**[!UICONTROL Content approved]**。
1. 在出现的&#x200B;**[!UICONTROL Edit]**&#x200B;窗口中，选择要重新启动的批准，然后单击&#x200B;**[!UICONTROL Re-initialize approval to submit it again]**。
1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;进行确认。

![](assets/offer_validate_013.png)

## 发布优惠{#publishing-the-offer}

优惠的内容和资格一经批准，优惠就会由一个工作流发布，该工作流会自动为其批准周期已结束的每个优惠运行。 **[!UICONTROL Offer notification]**&#x200B;工作流还每小时运行一次，以便将优惠目录中包含的空格和类别从设计环境同步（如果需要）到实时环境。

设计环境中可用优惠的仪表板包含有关发布的信息，包括实时环境中匹配优惠的名称。

![](assets/offer_golive_001.png)

要显示实时优惠中可用的优惠，请单击“环境”标签：实时优惠具有包含其所有相关信息的仪表板。

![](assets/offer_golive_002.png)

## 禁用优惠{#disabling-an-offer}

优惠获得批准后，您可以禁用它。

要执行此操作，请转到仪表板，查找联机优惠或等待联机的优惠，然后单击&#x200B;**[!UICONTROL Disable offer]**。

您还可以通过转到&#x200B;**[!UICONTROL Eligibility]**&#x200B;选项卡并选中&#x200B;**[!UICONTROL Enabled]**&#x200B;框直接禁用类别。

>[!NOTE]
>
>在设计环境中删除优惠时，该环境会在链接的在线中自动停用。 在提案保留期之后，停用的优惠从在线环境中删除。

![](assets/offer_preview_deactivate.png)

