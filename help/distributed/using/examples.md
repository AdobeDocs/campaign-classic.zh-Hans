---
product: campaign
title: 示例
description: 示例
audience: campaign
content-type: reference
topic-tags: distributed-marketing
exl-id: 2bef6b5e-887e-4c56-bb4b-3583472ca333
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 0%

---

# 示例{#examples}

![](../../assets/v7-only.svg)

## 创建本地营销活动（按表单） {#creating-a-local-campaign--by-form-}

**按形式**&#x200B;类型的Web界面涉及使用&#x200B;**Web应用程序**。 根据其配置，此Web应用程序可以包含任何类型的已定义个性化元素。 例如，您可以建议使用链接来评估目标、预算、内容等。 通过专用API。

>[!NOTE]
>
>API在专用文档中进行了详细介绍，具体访问方式取决于您的合同。 请参阅[API](../../configuration/using/about-web-services.md)。
>
>此示例中使用的Web应用程序不是随Adobe Campaign一起提供的现成Web应用程序。 要在营销活动中使用表单，必须创建专用的Web应用程序。

创建营销活动模板时，单击&#x200B;**[!UICONTROL Advanced campaign settings...]**&#x200B;链接&#x200B;**[!UICONTROL Web interface]**&#x200B;选项中的&#x200B;**[!UICONTROL Zoom]**&#x200B;图标，以访问Web应用程序的详细信息。

![](assets/mkg_dist_local_op_form1.png)

>[!NOTE]
>
>Web应用程序参数仅在营销活动模板中可用。

在&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡中，选择&#x200B;**促销活动顺序**&#x200B;活动并将其打开以访问其内容。

![](assets/mkg_dist_web_app1.png)

在此示例中，**促销活动顺序**&#x200B;活动包括：

* 地方实体在订单期间输入的字段，

   ![](assets/mkg_dist_web_app2.png)

* 允许本地实体评估营销活动的链接（例如目标、预算、内容等），

   ![](assets/mkg_dist_web_app3.png)

* 脚本，可用于计算和显示这些评估的结果。

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

## 创建协作型营销活动（通过目标批准） {#creating-a-collaborative-campaign--by-target-approval-}

### 简介 {#introduction}

您是一家大型服装品牌的营销经理，该品牌在美国各地拥有一家在线商店和几家专卖店。 春天到来后，你决定创建一个特惠，让你最好的客户在你的目录里把所有裙子都减掉50%。

此优惠针对的是您美国商店中最好的客户，即自年初以来已花费超过300美元的客户。

因此，您决定使用分布式营销创建协作式营销活动（按目标批准），以便您选择商店的最佳客户（按区域分组），该客户将收到包含特殊选件的电子邮件投放。

此示例的第一部分说明了接收促销活动创建通知的本地实体，以及它们如何使用该实体评估促销活动并对其进行排序。

此示例的第二部分说明如何创建营销活动。

步骤如下：

**对于本地实体**

1. 使用营销活动创建通知可访问中央实体选择的联系人列表。
1. 选择联系人并批准参与。

**对于中央实体：**

1. 创建&#x200B;**[!UICONTROL Data distribution]**&#x200B;活动。
1. 创建协作营销活动。
1. 发布营销活动。

### 本地实体端 {#local-entity-side}

1. 被选择参与营销活动的本地实体将收到电子邮件通知。

   ![](assets/mkg_dist_use_case_target_valid8.png)

1. 通过单击&#x200B;**[!UICONTROL Access your contact list and approve targeting]**&#x200B;链接，本地实体（通过Web浏览器）可以访问为营销活动选择的客户端列表。

   ![](assets/mkg_dist_use_case_target_valid9.png)

1. 本地实体从列表中取消检查某些联系人，因为自年初以来，已联系他们以获取类似优惠。

   ![](assets/mkg_dist_use_case_target_valid10.png)

检查获得批准后，营销活动可自动启动。

### 中央实体侧 {#central-entity-side}

#### 创建数据分发活动 {#creating-a-data-distribution-activity}

1. 要设置协作型营销活动（通过目标批准），您必须首先创建&#x200B;**[!UICONTROL Data distribution activity]**。 单击&#x200B;**[!UICONTROL Resources > Campaign management > Data distribution]**&#x200B;节点中的&#x200B;**[!UICONTROL New]**&#x200B;图标。

   ![](assets/mkg_dist_use_case_target_valid3.png)

1. 在&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，必须指定：

   * **[!UICONTROL Targeting dimension]**。 在此，对&#x200B;**收件人**&#x200B;执行&#x200B;**数据分发**。
   * **[!UICONTROL Distribution type]**。 您可以选择&#x200B;**固定大小**&#x200B;或&#x200B;**大小作为百分比**。
   * **[!UICONTROL Assignment type]**。 选择&#x200B;**本地实体**&#x200B;选项。
   * **[!UICONTROL Distribution type]**。 在此，收件人表中显示的&#x200B;**[!UICONTROL Origin (@origin)]**&#x200B;字段用于标识联系人与本地实体之间的关系。
   * **[!UICONTROL Approval storage]**&#x200B;字段。 选择&#x200B;**收件人的本地批准**&#x200B;选项。

1. 在&#x200B;**[!UICONTROL Breakdown]**&#x200B;选项卡中，指定：

   * **[!UICONTROL Distribution field value]**，对应于参与即将进行的营销活动的本地实体。
   * 本地实体&#x200B;**[!UICONTROL label]**。
   * **[!UICONTROL Size]**（固定或以百分比表示）。 **0的默认值**&#x200B;包括选择链接到本地实体的所有收件人。

   ![](assets/mkg_dist_use_case_target_valid4.png)

1. 保存新的数据分发。

#### 创建协作活动 {#creating-a-collaborative-campaign}

1. 从&#x200B;**[!UICONTROL Campaign management > Campaign]**&#x200B;节点中，创建新的&#x200B;**[!UICONTROL collaborative campaign (by target approval)]**。
1. 在&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;选项卡中，为营销活动创建工作流。 该活动必须包含&#x200B;**Split**&#x200B;活动，其中&#x200B;**[!UICONTROL Record count limitation]**&#x200B;由&#x200B;**[!UICONTROL Data distribution]**&#x200B;活动定义。

   ![](assets/mkg_dist_use_case_target_valid5.png)

1. 添加&#x200B;**[!UICONTROL Local approval]**&#x200B;操作，您可以在其中指定：

   * 将在通知中发送给本地实体的消息内容，
   * 批准提醒，
   * 营销活动的预期处理。

   ![](assets/mkg_dist_use_case_target_valid7.png)

1. 保存记录。

#### 发布营销活动 {#publishing-the-campaign}

您现在可以从&#x200B;**[!UICONTROL Campaigns]**&#x200B;选项卡添加&#x200B;**营销活动包**。

1. 选择&#x200B;**[!UICONTROL Reference campaign]**。 在资源包的&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡中，您可以选择&#x200B;**[!UICONTROL Approval mode]**&#x200B;用于营销活动：

   * 在&#x200B;**手动**&#x200B;模式中，如果本地实体接受中央实体的邀请，则它们会参与营销活动。 如果需要，他们可以删除预先选定的联系人，并且需要经理的批准才能确认他们参与营销活动。
   * 在&#x200B;**自动**&#x200B;模式下，本地实体必须参与营销活动，除非它们取消注册。 他们可以删除联系人，而无需批准。

   ![](assets/mkg_dist_use_case_target_valid.png)

1. 在&#x200B;**[!UICONTROL Description]**&#x200B;选项卡中，您可以添加营销活动的说明以及要发送到本地实体的任何文档。

   ![](assets/mkg_dist_use_case_target_valid1.png)

1. 批准您的营销活动包，然后启动发布该包的工作流，并将其提供给包列表中的所有本地实体。

   ![](assets/mkg_dist_use_case_target_valid2.png)

## 创建协作型营销活动（按表单） {#creating-a-collaborative-campaign--by-form-}

### 简介 {#introduction-1}

你是一家大型化妆品品牌的营销经理，该品牌在美国各地有一家网上商店和几家专卖店。 要卸下冬季库存并为新库存腾出空间，您决定创建一个特殊选件，以定位两个客户类别：30岁以上的人，你将向他们提供年龄敏感的护肤产品，30岁以下的人，你将向他们提供更基本的护肤产品。

因此，您决定使用分布式营销创建（按表单）的协作式营销活动，以便您能够根据年龄范围从不同商店选择客户。 这些客户将收到一封包含特殊优惠的电子邮件投放，该优惠将根据其年龄范围进行个性化。

此示例的第一部分说明了接收促销活动创建通知的本地实体，以及它们如何使用该实体评估促销活动并对其进行排序。

此示例的第二部分说明如何创建营销活动。

步骤如下：

**对于本地实体**

1. 使用营销活动创建通知访问在线表单。
1. 个性化营销活动（目标、内容、投放量）。
1. 检查这些字段，并根据需要更改它们。
1. 批准您的参与。
1. 本地实体（或中央实体）的经理会批准您的配置和参与。

**对于中央实体：**

1. 创建协作营销活动。
1. 像为本地营销活动配置&#x200B;**[!UICONTROL Advanced campaign settings...]**&#x200B;一样。
1. 像为本地营销活动配置营销活动工作流和投放一样。
1. 更新Web窗体。
1. 创建营销活动包并发布它。

### 本地实体端 {#local-entity-side-1}

1. 选择参加营销活动的本地实体会收到一封电子邮件通知，通知他们参与营销活动。

   ![](assets/mkg_dist_use_case_form_7.png)

1. 本地实体填写个性化表单，然后：

   * 评估目标和预算，
   * 预览投放内容，
   * 批准他们的参与。

      ![](assets/mkg_dist_use_case_form_8.png)

1. 负责验证订单的操作员批准其参与。

   ![](assets/mkg_dist_use_case_form_9.png)

### 中央实体侧 {#central-entity-side-1}

1. 要实施协作型营销活动（按表单），必须使用&#x200B;**协作型营销活动（按表单）**&#x200B;模板创建营销活动。

   ![](assets/mkg_dist_use_case_form_1.png)

1. 在营销活动的&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡中，单击&#x200B;**[!UICONTROL Advanced campaign settings...]**&#x200B;链接以将其配置为本地营销活动。 请参阅[创建本地营销活动（按表单）](#creating-a-local-campaign--by-form-)。

   ![](assets/mkg_dist_use_case_form_2.png)

1. 配置营销活动工作流和Web窗体。 请参阅[创建本地营销活动（按表单）](#creating-a-local-campaign--by-form-)。
1. 通过指定执行计划和涉及的本地实体来创建营销活动包。

   ![](assets/mkg_dist_use_case_form_3.png)

1. 通过在&#x200B;**[!UICONTROL Edit]**&#x200B;选项卡中选择批准模式来完成包配置。

   ![](assets/mkg_dist_use_case_form_4.png)

1. 在&#x200B;**[!UICONTROL Description]**&#x200B;选项卡中，您可以输入营销活动包描述、在发布营销活动包时将发送给本地实体的通知消息，以及将任何信息性文档附加到营销活动包。

   ![](assets/mkg_dist_use_case_form_5.png)

1. 批准包以发布它。

   ![](assets/mkg_dist_use_case_form_6.png)
