---
product: campaign
title: 批准和激活优惠
description: 批准和激活优惠
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: cf7649fe-f62a-4dfa-a19e-9c1ca545e3e3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 2%

---

# 批准和激活优惠{#approving-and-activating-an-offer}



选件内容完成后，您需要批准该内容，以便复制到实时环境中并投放。 批准涉及优惠内容及其资格。

优惠仪表板上的横幅会告诉您优惠是否需要经历批准周期。

![](assets/offer_validate_001.png)

## 批准优惠内容 {#approving-offer-content}

批准优惠内容意味着选择您希望在实时环境中可用的呈现方式。

选件的内容在每个空间中具有一个表示形式。 由于每个选件空间都有其自己的结构和渲染功能，因此选件表示可能会有所不同。

您可以选择批准某些可用空间上的选件内容，拒绝其他空间上的选件内容。

>[!IMPORTANT]
>
>选件的内容和资格获得批准后，发布工作流（选件通知）将自动运行，并且选件将在所有激活的空间中上线并可用。

要批准选件内容，请应用以下步骤：

1. 单击 **[!UICONTROL Approval]** 按钮并选择 **[!UICONTROL Approve content]** 在弹出窗口中。

   ![](assets/offer_validate_002.png)

1. 使用下拉列表，选择要继续编辑的表示法或要发布到实时环境的表示法，然后单击 **[!UICONTROL Content approval]**.

   ![](assets/offer_validate_003.png)

   在批准优惠内容后，将在优惠仪表板表格中更新信息。

   ![](assets/offer_validate_004.png)

   >[!NOTE]
   >
   >此 **[!UICONTROL Content approved]** 提及这并不意味着已启用并批准所有优惠呈现。 它指示内容批准流程已完成，无论是否已启用/批准所有选件。

## 批准优惠资格 {#approving-offer-eligibility}

批准优惠资格意味着接受或拒绝优惠权重，以及同样在优惠中配置或者继承自父类别中创建的规则的资格规则。

>[!IMPORTANT]
>
>选件的内容和资格获得批准后，发布工作流（选件通知）将自动运行，并且选件将在所有激活的空间中上线并可用。

* 通过单击可查看规则的完整列表 **[!UICONTROL Schedule and eligibility rules]**.

   ![](assets/offer_validate_005.png)

* 要更改资格规则，请单击 **[!UICONTROL Reject]**，然后单击 **[!UICONTROL Eligibility approval]**.

   ![](assets/offer_validate_007.png)

   优惠仪表板上的各种状态都会更新。

   ![](assets/offer_validate_006.png)

* 要接受优惠资格，请单击 **[!UICONTROL Approve eligibility]**.

   ![](assets/offer_validate_008.png)

   批准资格，根据需要添加评论，然后单击 **[!UICONTROL Eligibility approval]**.

   ![](assets/offer_validate_009.png)

   优惠仪表板上的各种状态都会更新。

   ![](assets/offer_validate_010.png)

## 审批跟踪 {#approval-tracking}

审批跟踪在优惠仪表板上可用。 单击 **[!UICONTROL Hide/display logs]** 以访问它。

![](assets/offer_validate_012.png)

>[!NOTE]
>
>跟踪也可在以下位置获取： **[!UICONTROL Audit]** 选项卡中，其中包含查看者注释的详细信息。

## 重新开始审批 {#restart-the-approval}

启动批准后，可将其重新启动。 为此，请按照以下说明操作：

1. 单击 **[!UICONTROL Content approved]** 在优惠仪表板上。
1. 在 **[!UICONTROL Edit]** 窗口中，选择要重新启动的批准，然后单击 **[!UICONTROL Re-initialize approval to submit it again]**.
1. 单击确认 **[!UICONTROL Ok]**.

![](assets/offer_validate_013.png)

## 发布优惠 {#publishing-the-offer}

选件的内容和资格获得批准后，选件将通过工作流发布，该工作流会为其批准周期结束的每个选件自动运行。 此 **[!UICONTROL Offer notification]** 工作流还每小时运行一次，以便将（如有必要）优惠目录中包含的空间和类别从设计环境同步到实时环境。

设计环境中可用选件的功能板包含有关发布的信息，包括实时环境中匹配选件的名称。

![](assets/offer_golive_001.png)

要显示实时环境中可用的选件，请单击选件标签：实时选件具有一个包含其所有相关信息的功能板。

![](assets/offer_golive_002.png)

## 禁用选件 {#disabling-an-offer}

选件获得批准后，您可以将其禁用。

为此，请转到仪表板以获取联机选件或等待联机选件，然后单击 **[!UICONTROL Disable offer]**.

您还可以通过转到 **[!UICONTROL Eligibility]** 选项卡并检查 **[!UICONTROL Enabled]** 盒子。

>[!NOTE]
>
>在设计环境中删除选件时，将在链接的在线环境中自动取消激活该选件。 在建议保留期过后，将从在线环境中删除停用的选件。

![](assets/offer_preview_deactivate.png)
