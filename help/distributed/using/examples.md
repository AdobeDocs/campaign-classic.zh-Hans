---
product: campaign
title: 分布式营销示例
description: 分布式营销示例
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Distributed Marketing
exl-id: 2bef6b5e-887e-4c56-bb4b-3583472ca333
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1293'
ht-degree: 0%

---

# 分布式营销示例{#distributed-marketing-samples}



## 创建本地活动（按表单） {#creating-a-local-campaign--by-form-}

此 **按表单** 类型web界面涉及使用 **Web应用程序**. 根据配置，此Web应用程序可以包含任何类型的已定义的个性化元素。 例如，您可以建议用于评估目标、预算、内容等的链接。 通过专用API。

>[!NOTE]
>
>在专用文档中详细介绍了API。 [了解详情](../../configuration/using/about-web-services.md)。
>
>本示例中使用的Web应用程序不是随Adobe Campaign一起提供的现成Web应用程序。 要在营销策划中使用表单，您必须创建专用的Web应用程序。

创建活动模板时，单击 **[!UICONTROL Zoom]** 中的图标 **[!UICONTROL Web interface]** 的选项 **[!UICONTROL Advanced campaign settings...]** 用于访问Web应用程序详细信息的链接。

![](assets/mkg_dist_local_op_form1.png)

>[!NOTE]
>
>Web应用程序参数仅在营销活动模板中可用。

在 **[!UICONTROL Edit]** 选项卡，选择 **营销活动订单** 并打开它以访问其内容。

![](assets/mkg_dist_web_app1.png)

在此示例中， **营销活动订单** 活动包括：

* 要由本地实体在订单期间输入的字段，

   ![](assets/mkg_dist_web_app2.png)

* 允许本地实体评估营销活动（例如目标、预算、内容等）的链接，

   ![](assets/mkg_dist_web_app3.png)

* 用于计算和显示这些评估结果的脚本。

   ![](assets/mkg_dist_web_app4.png)

在此示例中，使用了以下API：

* 对于目标评估，

   ```
   var res = nms.localOrder.EvaluateTarget(ctx.localOrder);
   ```

* 对于预算评估，

   ```
   var res = nms.localOrder.EvaluateDeliveryBudget(ctx.@deliveryId, NL.XTK.parseNumber(ctx.@compt));
   ```

* 对于内容评估，

   ```
   var res = nms.localOrder.EvaluateContent(ctx.localOrder, ctx.@deliveryId, "html", resSeed.@id);
   ```

## 创建协作活动（通过目标审批） {#creating-a-collaborative-campaign--by-target-approval-}

### 简介 {#introduction}

您是一家大型服装品牌的营销经理，该品牌在美国拥有一家网上商店和几家精品店。 春天到了，你决定推出一项特别优惠，给最优秀的客户目录中的所有服装打50%的优惠。

这项优惠针对的是您美国商店的最优秀客户，也就是说自今年初以来已花费300多美元的客户。

因此，您决定使用分布式营销来创建一个协作营销活动（按目标批准），该活动允许您选择商店的最佳客户（按区域分组），这些客户将收到包含特殊优惠的电子邮件投放。

此示例的第一部分说明了接收促销活动创建通知的本地实体，以及如何使用它来评估促销活动并对其进行排序。

此示例的第二部分说明如何创建营销策划。

步骤如下：

**对于本地实体**

1. 使用营销活动创建通知访问中央实体选择的联系人列表。
1. 选择联系人并批准参与率。

**对于中央实体：**

1. 创建 **[!UICONTROL Data distribution]** 活动。
1. 创建协作活动。
1. 发布营销活动。

### 本地实体侧 {#local-entity-side}

1. 已选择参与营销活动的本地实体将收到电子邮件通知。

   ![](assets/mkg_dist_use_case_target_valid8.png)

1. 通过单击 **[!UICONTROL Access your contact list and approve targeting]** 链接，则授予本地实体访问（通过Web浏览器）为营销活动选择的客户端列表的权限。

   ![](assets/mkg_dist_use_case_target_valid9.png)

1. 本地实体将从列表中取消选中某些联系人，因为自年初以来，已就类似的选件与他们进行了联系。

   ![](assets/mkg_dist_use_case_target_valid10.png)

检查获得批准后，营销活动即可自动启动。

### 中央实体侧 {#central-entity-side}

#### 创建数据分发活动 {#creating-a-data-distribution-activity}

1. 要设置协作活动（通过目标审批），您必须首先创建 **[!UICONTROL Data distribution activity]**. 单击 **[!UICONTROL New]** 中的图标 **[!UICONTROL Resources > Campaign management > Data distribution]** 节点。

   ![](assets/mkg_dist_use_case_target_valid3.png)

1. 在 **[!UICONTROL General]** 选项卡，您必须指定：

   * 此 **[!UICONTROL Targeting dimension]**. 此处 **数据分发** 在 **收件人**.
   * 此 **[!UICONTROL Distribution type]**. 您可以选择 **固定大小** 或 **以百分比显示的大小**.
   * 此 **[!UICONTROL Assignment type]**. 选择 **本地实体** 选项。
   * 此 **[!UICONTROL Distribution type]**. 在这里，它是 **[!UICONTROL Origin (@origin)]** 收件人表中存在的字段，用于标识联系人和本地实体之间的关系。
   * 此 **[!UICONTROL Approval storage]** 字段。 选择 **收件人的本地审批** 选项。

1. 在 **[!UICONTROL Breakdown]** 选项卡，指定：

   * 此 **[!UICONTROL Distribution field value]**，对应于即将推出的营销活动中涉及的本地实体。
   * 本地实体 **[!UICONTROL label]**.
   * 此 **[!UICONTROL Size]** （固定或百分比）。 此 **0默认值** 涉及选择链接到本地实体的所有收件人。

   ![](assets/mkg_dist_use_case_target_valid4.png)

1. 保存您的新数据分发。

#### 创建协作活动 {#creating-a-collaborative-campaign}

1. 从 **[!UICONTROL Campaign management > Campaign]** 节点，新建 **[!UICONTROL collaborative campaign (by target approval)]**.
1. 在 **[!UICONTROL Targeting and workflows]** 选项卡，为您的营销活动创建工作流。 此必须包含 **Split** 活动，其中 **[!UICONTROL Record count limitation]** 由 **[!UICONTROL Data distribution]** 活动。

   ![](assets/mkg_dist_use_case_target_valid5.png)

1. 添加 **[!UICONTROL Local approval]** 操作，您可以在其中指定：

   * 消息内容将被发送到通知中的本地实体，
   * 审批提醒，
   * 营销活动的预期处理。

   ![](assets/mkg_dist_use_case_target_valid7.png)

1. 保存您的记录。

#### 发布营销活动 {#publishing-the-campaign}

您现在可以添加 **营销活动包** 从 **[!UICONTROL Campaigns]** 选项卡。

1. 选择您的 **[!UICONTROL Reference campaign]**. 在 **[!UICONTROL Edit]** 选项卡中，您可以选择 **[!UICONTROL Approval mode]** 要用于您的营销活动，请执行以下操作：

   * 在 **手动** 模式，如果本地实体接受来自中央实体的邀请，则参与该活动。 如果他们想要并且需要经理的批准来确认他们参与促销活动，则可以删除预先选定的联系人。
   * 在 **自动** 模式，本地实体必须参与活动，除非它们从活动中注销自己。 他们无需批准即可删除联系人。

   ![](assets/mkg_dist_use_case_target_valid.png)

1. 在 **[!UICONTROL Description]** 选项卡，您可以添加营销活动的描述以及要发送到本地实体的任何文档。

   ![](assets/mkg_dist_use_case_target_valid1.png)

1. 批准活动包，然后启动工作流以发布包，并使其对包列表中的所有本地实体可用。

   ![](assets/mkg_dist_use_case_target_valid2.png)

## 创建协作活动（按表单） {#creating-a-collaborative-campaign--by-form-}

### 简介 {#introduction-1}

你是一家大型化妆品牌的市场经理，该品牌在美国有一家在线商店和几家精品店。 为了卸掉冬季库存并为新库存腾出空间，您决定创建一个特别优惠，该优惠将针对两类客户：30岁以上的客户，您将向其提供对年龄敏感的护肤产品；以及30岁以下客户，您将向其提供更基本的护肤产品。

因此，您决定使用分布式营销来创建一个协作营销活动（按表单），该活动允许您按年龄范围从不同的商店中选择客户。 这些客户将收到包含特殊优惠的电子邮件投放，该优惠将根据其年龄范围进行个性化。

此示例的第一部分说明了接收促销活动创建通知的本地实体，以及如何使用它来评估促销活动并对其进行排序。

此示例的第二部分说明如何创建营销策划。

步骤如下：

**对于本地实体**

1. 使用营销活动创建通知访问在线表单。
1. 个性化营销活动（目标、内容、投放量）。
1. 检查这些字段，并在必要时进行更改。
1. 批准您的参与。
1. 本地实体（或中央实体）的经理批准您的配置和参与。

**对于中央实体：**

1. 创建协作活动。
1. 配置 **[!UICONTROL Advanced campaign settings...]** 就象你参加本地活动一样。
1. 像配置本地营销活动一样，配置营销活动工作流和投放。
1. 更新Web窗体。
1. 创建并发布营销活动包。

### 本地实体侧 {#local-entity-side-1}

1. 被选择参加营销策划的本地实体收到电子邮件通知，告知他们已参加营销策划。

   ![](assets/mkg_dist_use_case_form_7.png)

1. 本地实体完成个性化表单，然后他们：

   * 评估目标和预算，
   * 预览投放内容，
   * 批准其参与。

      ![](assets/mkg_dist_use_case_form_8.png)

1. 负责验证订单的操作员批准其参与。

   ![](assets/mkg_dist_use_case_form_9.png)

### 中央实体侧 {#central-entity-side-1}

1. 要实施协作营销活动（按表单），您必须使用 **协作营销活动（按表单）** 模板。

   ![](assets/mkg_dist_use_case_form_1.png)

1. 在营销活动的 **[!UICONTROL Edit]** 选项卡，单击 **[!UICONTROL Advanced campaign settings...]** 将其配置为本地营销活动的链接。 请参阅 [创建本地活动（按表单）](#creating-a-local-campaign--by-form-).

   ![](assets/mkg_dist_use_case_form_2.png)

1. 配置营销活动工作流和Web窗体。 请参阅 [创建本地活动（按表单）](#creating-a-local-campaign--by-form-).
1. 通过指定执行计划和所涉及的本地实体来创建您的Campaign包。

   ![](assets/mkg_dist_use_case_form_3.png)

1. 通过在以下位置选择批准模式，最终完成包配置： **[!UICONTROL Edit]** 选项卡。

   ![](assets/mkg_dist_use_case_form_4.png)

1. 从 **[!UICONTROL Description]** 选项卡，您可以输入campaign包说明、在发布包时发送到本地实体的通知消息，并将任何信息性文档附加到campaign包。

   ![](assets/mkg_dist_use_case_form_5.png)

1. 批准包以发布它。

   ![](assets/mkg_dist_use_case_form_6.png)
