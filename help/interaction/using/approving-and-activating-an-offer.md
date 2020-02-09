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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 215e4d1ca78938b38b53cae0357612deebf7727b

---


# 批准和激活优惠{#approving-and-activating-an-offer}

完成选件内容后，您需要批准该内容，以将其复制到实时环境中并交付。 批准涉及优惠内容及其资格。

选件功能板上的横幅告诉您选件是否需要通过批准周期。

![](assets/offer_validate_001.png)

## 批准优惠内容 {#approving-offer-content}

批准优惠内容意味着选择要在实时环境中提供的表示形式。

选件的内容每个空间有一个表示形式。 由于每个选件空间都有其自己的结构和自己的渲染功能，因此选件表示形式可能会有所不同。

您可以选择在某些可用空间上批准选件内容并在其他空间上拒绝它。

>[!CAUTION]
>
>一旦某个选件的内容和资格获得批准，发布工作流（选件通知）将自动运行，并且该选件将变为实时并且在所有激活的空间上可用。

要批准选件内容，请应用以下步骤：

1. 单击该按 **[!UICONTROL Approval]** 钮并在弹出窗 **[!UICONTROL Approve content]** 口中选择。

   ![](assets/offer_validate_002.png)

1. 使用下拉列表，选择要继续编辑的表示或要发布到实时环境的表示，然后单击 **[!UICONTROL Content approval]**。

   ![](assets/offer_validate_003.png)

   一旦选件内容获得批准，信息便会更新在选件功能板表上。

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >提 **[!UICONTROL Content approved]** 及并不表示已启用和批准所有选件陈述。 它表示内容批准过程已经完成，无论是否已启用／批准所有选件。

## 批准优惠资格 {#approving-offer-eligibility}

批准优惠资格是指接受或拒绝优惠权重以及在优惠中配置或从父类别中创建的规则继承的资格规则。

>[!CAUTION]
>
>一旦某个选件的内容和资格获得批准，发布工作流（选件通知）将自动运行，并且该选件将变为实时并且在所有激活的空间上可用。

* 可通过单击查看规则的完整列表 **[!UICONTROL Schedule and eligibility rules]**。

   ![](assets/offer_validate_005.png)

* 要更改资格规则，请单击， **[!UICONTROL Reject]**&#x200B;然后单击 **[!UICONTROL Eligibility approval]**。

   ![](assets/offer_validate_007.png)

   选件功能板上会更新各种状态。

   ![](assets/offer_validate_006.png)

* 要接受选件资格，请单击 **[!UICONTROL Approve eligibility]**。

   ![](assets/offer_validate_008.png)

   批准资格，根据需要添加评论，然后单击 **[!UICONTROL Eligibility approval]**。

   ![](assets/offer_validate_009.png)

   选件功能板上会更新各种状态。

   ![](assets/offer_validate_010.png)

## 批准跟踪 {#approval-tracking}

优惠控制板上提供了批准跟踪功能。 单击 **[!UICONTROL Hide/display logs]** 可访问它。

![](assets/offer_validate_012.png)

>[!NOTE]
>
>还可以在选件的选项卡 **[!UICONTROL Audit]** 中进行跟踪，并提供审阅者注释的详细信息。

## 重新启动批准 {#restart-the-approval}

一旦启动批准，即可重新启动它。 为此，请按照以下说明操作：

1. 单击 **[!UICONTROL Content approved]** 选件功能板。
1. 在显示 **[!UICONTROL Edit]** 的窗口中，选择要重新启动的批准，然后单击 **[!UICONTROL Re-initialize approval to submit it again]**。
1. 单击进行确 **[!UICONTROL Ok]**&#x200B;认。

![](assets/offer_validate_013.png)

## 发布选件 {#publishing-the-offer}

一旦某个选件的内容和资格均获得批准，该选件将由一个工作流发布，该工作流会自动为其批准周期已结束的每个选件运行。 该工 **[!UICONTROL Offer notification]** 作流还每小时运行一次，以便从设计环境同步（如有必要）选件目录中包含的空间和类别到实时环境。

设计环境中可用选件的仪表板包含有关发布的信息，包括实时环境中匹配选件的名称。

![](assets/offer_golive_001.png)

要显示实时环境中可用的选件，请单击选件标签：实时选件有一个包含其所有相关信息的仪表板。

![](assets/offer_golive_002.png)

## 禁用选件 {#disabling-an-offer}

优惠一旦获得批准，您就可以禁用它。

为此，请转至仪表板，查看联机选件或等待联机的选件，然后单击 **[!UICONTROL Disable offer]**。

您还可以通过转到选项卡并选中该框直 **[!UICONTROL Eligibility]** 接禁用类 **[!UICONTROL Enabled]** 别。

>[!NOTE]
>
>在设计环境中删除选件后，该选件会在链接的在线环境中自动取消激活。 在提议保留期后，取消激活的优惠将从在线环境中删除。

![](assets/offer_preview_deactivate.png)

