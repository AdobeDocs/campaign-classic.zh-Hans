---
product: campaign
title: 批准和激活优惠
description: 批准和激活优惠
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: cf7649fe-f62a-4dfa-a19e-9c1ca545e3e3
source-git-commit: d835da6c7b55d9bf70b6b5dc58880718e12211d5
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 2%

---

# 批准和激活优惠{#approving-and-activating-an-offer}

![](../../assets/common.svg)

选件内容完成后，您需要批准该内容以将其复制到实时环境中并进行交付。 批准涉及选件内容及其资格。

选件仪表板上的横幅可告知您选件是否需要经过批准周期。

![](assets/offer_validate_001.png)

## 批准优惠内容 {#approving-offer-content}

批准选件内容意味着选择要在实时环境中提供的表示形式。

选件的内容在每个空间中具有一个表示形式。 由于每个选件空间都有其自己的结构和自己的渲染功能，因此选件表示方式可能会有所不同。

您可以选择在某些可用空间上批准选件内容，而在其他空间上拒绝该选件内容。

>[!IMPORTANT]
>
>选件的内容和资格获得批准后，发布工作流程（选件通知）将自动运行，并且该选件会处于活跃状态并在所有激活的空间上可用。

要批准选件内容，请应用以下步骤：

1. 单击 **[!UICONTROL Approval]** 按钮，选择 **[!UICONTROL Approve content]** 中。

   ![](assets/offer_validate_002.png)

1. 使用下拉列表，选择要编辑的表示法或要发布到实时环境的表示法，然后单击 **[!UICONTROL Content approval]**.

   ![](assets/offer_validate_003.png)

   选件内容获得批准后，信息会在选件功能板表格中进行更新。

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >的 **[!UICONTROL Content approved]** 提及并不意味着已启用并批准所有选件表示形式。 它表示内容批准流程已完成，无论是否已启用/批准所有选件。

## 批准优惠资格 {#approving-offer-eligibility}

批准选件资格是指接受或拒绝选件权重以及在选件中配置或从父类别中创建的规则继承的资格规则。

>[!IMPORTANT]
>
>选件的内容和资格获得批准后，发布工作流程（选件通知）将自动运行，并且该选件会处于活跃状态并在所有激活的空间上可用。

* 可以通过单击 **[!UICONTROL Schedule and eligibility rules]**.

   ![](assets/offer_validate_005.png)

* 要更改资格规则，请单击 **[!UICONTROL Reject]**，然后单击 **[!UICONTROL Eligibility approval]**.

   ![](assets/offer_validate_007.png)

   选件功能板上的各种状态已更新。

   ![](assets/offer_validate_006.png)

* 要接受选件资格，请单击 **[!UICONTROL Approve eligibility]**.

   ![](assets/offer_validate_008.png)

   批准资格，根据需要添加评论，然后单击 **[!UICONTROL Eligibility approval]**.

   ![](assets/offer_validate_009.png)

   选件功能板上的各种状态已更新。

   ![](assets/offer_validate_010.png)

## 批准跟踪 {#approval-tracking}

批准跟踪可在选件功能板中使用。 单击 **[!UICONTROL Hide/display logs]** 来访问它。

![](assets/offer_validate_012.png)

>[!NOTE]
>
>在 **[!UICONTROL Audit]** 选项卡，其中包含审阅人评论的详细信息。

## 重新启动批准 {#restart-the-approval}

启动批准后，即可重新启动该批准。 为此，请按照以下说明操作：

1. 单击 **[!UICONTROL Content approved]** 选件功能板中。
1. 在 **[!UICONTROL Edit]** 显示的窗口中，选择要重新启动的批准，然后单击 **[!UICONTROL Re-initialize approval to submit it again]**.
1. 单击以确认 **[!UICONTROL Ok]**.

![](assets/offer_validate_013.png)

## 发布选件 {#publishing-the-offer}

选件的内容和资格均获得批准后，该选件将通过一个工作流程发布，该工作流程会为其批准周期已完成的每个选件自动运行。 的 **[!UICONTROL Offer notification]** 工作流还每小时运行一次，以便从设计环境同步（如有必要）选件目录中包含的空间和类别到实时环境。

设计环境中可用选件的功能板包含有关发布的信息，包括实时环境中匹配选件的名称。

![](assets/offer_golive_001.png)

要显示实时环境中可用的选件，请单击选件标签：实时选件有一个包含其所有相关信息的功能板。

![](assets/offer_golive_002.png)

## 禁用选件 {#disabling-an-offer}

选件获得批准后，即可将其禁用。

要实现此目的，请转到功能板以获取在线选件或等待联机的选件，然后单击 **[!UICONTROL Disable offer]**.

您还可以通过转到 **[!UICONTROL Eligibility]** 选项卡并选中 **[!UICONTROL Enabled]** 框中。

>[!NOTE]
>
>在设计环境中删除某个选件后，该选件会在链接的在线环境中自动停用。 在建议保留期后，将从在线环境中删除已停用的选件。

![](assets/offer_preview_deactivate.png)
