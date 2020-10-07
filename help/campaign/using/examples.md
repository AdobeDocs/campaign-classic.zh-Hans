---
title: 示例
seo-title: 示例
description: 示例
seo-description: null
page-status-flag: never-activated
uuid: bfc9bb13-500b-4435-b56a-550588a240bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: distributed-marketing
discoiquuid: 7b0aef75-345d-45be-b7d0-a9f6944ee678
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1298'
ht-degree: 0%

---


# 示例{#examples}

## 创建本地活动（按表单） {#creating-a-local-campaign--by-form-}

按 **表单类** 型Web界面涉及使 **用Web 应用程序**。 根据其配置，此Web 应用程序可以包含任何类型的已定义个性化元素。 例如，您可以建议使用链接来评估目标、预算、内容等。 通过专用API。

>[!NOTE]
>
>API在专用文档中详细介绍，其访问权限取决于您的合同。 请参阅 [API](../../configuration/using/about-web-services.md)。
>
>此示例中使用的Web 应用程序不是附带Adobe Campaign的现成Web应用程序。 要在活动中使用表单，您必须创建专用Web 应用程序。

创建活动模板时，单击 **[!UICONTROL Zoom]** 链接选项 **[!UICONTROL Web interface]** 中的图 **[!UICONTROL Advanced campaign settings...]** 标以访问Web 应用程序的详细信息。

![](assets/mkg_dist_local_op_form1.png)

>[!NOTE]
>
>Web 应用程序参数仅在活动模板中可用。

在标 **[!UICONTROL Edit]** 签中，选择 **活动顺序** 活动并打开它以访问其内容。

![](assets/mkg_dist_web_app1.png)

在此示例中，活动 **订单** 活动包括：

* 本地实体在订单中输入的字段，

   ![](assets/mkg_dist_web_app2.png)

* 允许本地实体评估活动的链接(例如目标、预算、内容等),

   ![](assets/mkg_dist_web_app3.png)

* 可用于计算和显示这些评估结果的脚本。

   ![](assets/mkg_dist_web_app4.png)

在此示例中，使用了以下API:

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

## 创建协作活动(通过目标批准) {#creating-a-collaborative-campaign--by-target-approval-}

### 简介 {#introduction}

您是一家大型服装品牌的营销经理，该品牌在美国各地拥有一家在线商店和几家专卖店。 春天来临后，您决定创建一个特殊优惠，为最佳客户提供目录中所有服装的五折优惠。

此优惠针对的是您美国商店的最佳客户，即年初以来花费超过300美元的客户。

因此，您决定使用分布式营销创建协作活动(通过目标批准)，这样您就可以选择商店的最佳客户（按区域分组），客户将收到包含特殊优惠的电子邮件投放。

此示例的第一部分说明了收到本地实体创建通知的活动，以及他们如何使用通知来评估活动和对其排序。

本示例的第二部分介绍如何创建活动。

步骤如下：

**对于本地实体**

1. 使用活动创建通知访问中央实体选择的联系人的列表。
1. 选择联系人并批准参与。

**对于中央实体:**

1. 创建 **[!UICONTROL Data distribution]** 活动
1. 创建协作活动。
1. 发布活动。

### 本地实体 {#local-entity-side}

1. 已选择参与本地实体的活动将收到电子邮件通知。

   ![](assets/mkg_dist_use_case_target_valid8.png)

1. 通过单击链 **[!UICONTROL Access your contact list and approve targeting]** 接，本地实体可以（通过Web浏览器）访问为活动选择的客户机的列表。

   ![](assets/mkg_dist_use_case_target_valid9.png)

1. 本地实体取消检查列表的某些联系人，因为自该年开始以来，已联系他们寻求类似优惠。

   ![](assets/mkg_dist_use_case_target_valid10.png)

检查获得批准后，活动可以自动开始。

### 中央实体 {#central-entity-side}

#### 创建数据分发活动 {#creating-a-data-distribution-activity}

1. 要设置协作活动(通过目标批准)，您必须先创建协作 **[!UICONTROL Data distribution activity]**。 单击节 **[!UICONTROL New]** 点中的 **[!UICONTROL Resources > Campaign management > Data distribution]** 图标。

   ![](assets/mkg_dist_use_case_target_valid3.png)

1. 在选项卡 **[!UICONTROL General]** 中，您必须指定：

   * the **[!UICONTROL Targeting dimension]**. 此处 **对收件人** 进行数据分 **发**。
   * the **[!UICONTROL Distribution type]**. 您可以选择固 **定大小** ，或 **大小作为百分比**。
   * the **[!UICONTROL Assignment type]**. 选择 **本地实体** 选项。
   * the **[!UICONTROL Distribution type]**. 此处是收件人表 **[!UICONTROL Origin (@origin)]** 中的字段，用于识别联系人与本地实体之间的关系。
   * 字 **[!UICONTROL Approval storage]** 段。 选择“ **本地批准收件人** ”选项。

1. In the **[!UICONTROL Breakdown]** tab, specify:

   * 这 **[!UICONTROL Distribution field value]**&#x200B;与即将到来的活动中的本地实体相对应。
   * 本地实体 **[!UICONTROL label]**。
   * ( **[!UICONTROL Size]** 固定或百分比)。 0 **默认值** ，包括选择链接到该本地实体的所有收件人。

   ![](assets/mkg_dist_use_case_target_valid4.png)

1. 保存新数据分发。

#### 创建协作活动 {#creating-a-collaborative-campaign}

1. 从节 **[!UICONTROL Campaign management > Campaign]** 点创建新 **[!UICONTROL collaborative campaign (by target approval)]**。
1. 在选项卡 **[!UICONTROL Targeting and workflows]** 中，为您的活动创建工作流。 它必须包含 **Split** 活动，该 **[!UICONTROL Record count limitation]** 由活动定义 **[!UICONTROL Data distribution]** 。

   ![](assets/mkg_dist_use_case_target_valid5.png)

1. 添加可 **[!UICONTROL Local approval]** 以指定的操作：

   * 发送给通知中本地实体的消息内容，
   * 批准提醒，
   * 活动的预期处理。

   ![](assets/mkg_dist_use_case_target_valid7.png)

1. 保存您的记录。

#### 发布活动 {#publishing-the-campaign}

您现在可以添加 **活动** ，来自 **活动世** 界。

1. 选择您的 **[!UICONTROL Reference campaign]**&#x200B;产品。 在包 **[!UICONTROL Edit]** 的选项卡中，您可以选择要 **[!UICONTROL Approval mode]** 用于活动的：

   * 在“ **手动** ”模式下，如果本地实体接受中央实体的邀请，则他们将参与活动。 如果需要，他们可以删除预先选择的联系人，并且需要经理的批准才能确认其参与活动。
   * 在自 **动模式** 中，本地实体必须参与活动，除非他们注销自己。 他们无需批准即可删除联系人。

   ![](assets/mkg_dist_use_case_target_valid.png)

1. 在选 **[!UICONTROL Description]** 项卡中，您可以添加活动的描述以及要发送给本地实体的任何文档。

   ![](assets/mkg_dist_use_case_target_valid1.png)

1. 批准您的活动包，然后开始您的工作流以发布该包，并使其可用于包列表中的所有本地实体。

   ![](assets/mkg_dist_use_case_target_valid2.png)

## 创建协作活动（按表单） {#creating-a-collaborative-campaign--by-form-}

### 简介 {#introduction-1}

您是一家大型化妆品品牌的营销经理，该品牌在美国各地拥有一家在线商店和几家专卖店。 要卸载冬季库存并腾出新库存空间，您决定创建一个特殊优惠,目标两个客户类别:30岁以上的人，你将优惠年龄敏感护肤产品，30岁以下的人，你将优惠更基本的护肤产品。

因此，您决定使用分布式营销创建协作活动（按表单），这样您可以根据年龄范围从不同商店选择客户。 这些客户将收到一封电子邮件投放，其中包含根据年龄范围个性化的特殊优惠。

此示例的第一部分说明了收到本地实体创建通知的活动，以及他们如何使用通知来评估活动和对其排序。

本示例的第二部分介绍如何创建活动。

步骤如下：

**对于本地实体**

1. 使用活动创建通知访问联机表单。
1. 个性化活动(目标、内容、投放量)。
1. 检查这些字段，并根据需要更改它们。
1. 批准您的参与。
1. 本地实体(或中央实体)经理批准您的配置和参与。

**对于中央实体:**

1. 创建协作活动。
1. 像为 **[!UICONTROL Advanced campaign settings...]** 本地活动配置一样配置。
1. 像配置本地活动一样配置投放工作流和活动。
1. 更新Web表单。
1. 创建活动包并发布它。

### 本地实体 {#local-entity-side-1}

1. 选择参与活动的本地实体会收到电子邮件通知，通知他们参与活动。

   ![](assets/mkg_dist_use_case_form_7.png)

1. 本地实体填写了个性化表单，然后：

   * 评估目标和预算，
   * 预览投放内容，
   * 批准其参与。

      ![](assets/mkg_dist_use_case_form_8.png)

1. 负责验证订单的操作员批准其参与。

   ![](assets/mkg_dist_use_case_form_9.png)

### 中央实体 {#central-entity-side-1}

1. 要实施协作活动（按表单），必须使用协作活动(按表 **单)模板创建活动** 。

   ![](assets/mkg_dist_use_case_form_1.png)

1. 在活动的选 **[!UICONTROL Edit]** 项卡中，单 **[!UICONTROL Advanced campaign settings...]** 击链接以将其配置为本地活动。 请参阅 [创建本地活动（按表单）](#creating-a-local-campaign--by-form-)。

   ![](assets/mkg_dist_use_case_form_2.png)

1. 配置活动工作流和Web表单。 请参阅 [创建本地活动（按表单）](#creating-a-local-campaign--by-form-)。
1. 通过指定执行活动和相关本地实体创建您的计划包。

   ![](assets/mkg_dist_use_case_form_3.png)

1. 通过在选项卡中选择批准模式来完成包 **[!UICONTROL Edit]** 配置。

   ![](assets/mkg_dist_use_case_form_4.png)

1. 在选项 **[!UICONTROL Description]** 卡中，您可以输入活动包描述，在发布包时向本地实体发送通知消息，并将任何信息文档附加到活动包。

   ![](assets/mkg_dist_use_case_form_5.png)

1. 批准要发布的包。

   ![](assets/mkg_dist_use_case_form_6.png)

