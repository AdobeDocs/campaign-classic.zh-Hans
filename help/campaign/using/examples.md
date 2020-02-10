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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 示例{#examples}

## 创建本地营销活动（按表单） {#creating-a-local-campaign--by-form-}

“按 **表单类型** ”Web界面涉及使用 **Web应用程序**。 根据其配置，此Web应用程序可以包含任何类型定义的个性化元素。 例如，您可以建议链接以评估目标、预算、内容等。 通过专用API。

>[!NOTE]
>
>API在专用文档中有详细介绍，其访问权限取决于您的合同。 请参阅 [API](../../configuration/using/about-web-services.md)。

>[!NOTE]
>
>此示例中使用的Web应用程序不是随Adobe Campaign一起推出的Web应用程序。 要在营销活动中使用表单，您必须创建专用的Web应用程序。

创建营销活动模板时，单击链 **[!UICONTROL Zoom]** 接选项中的图 **[!UICONTROL Web interface]** 标以访 **[!UICONTROL Advanced campaign settings...]** 问Web应用程序的详细信息。

![](assets/mkg_dist_local_op_form1.png)

>[!NOTE]
>
>Web应用程序参数仅在营销活动模板中可用。

在选项 **[!UICONTROL Edit]** 卡中，选择 **Campaign订单活动** ，然后打开它以访问其内容。

![](assets/mkg_dist_web_app1.png)

在此示例中，系列活 **动订单** (Campaign order)活动包括：

* 要由本地实体在订单期间输入的字段，

   ![](assets/mkg_dist_web_app2.png)

* 允许本地实体评估营销活动的链接（例如目标、预算、内容等）,

   ![](assets/mkg_dist_web_app3.png)

* 允许您计算和显示这些评估结果的脚本。

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

## 创建协作营销活动（通过目标批准） {#creating-a-collaborative-campaign--by-target-approval-}

### 简介 {#introduction}

您是一家大型服装品牌的营销经理，该品牌在美国各地拥有一家在线商店和几家精品店。 春天到来后，您决定创建一个特价优惠，让最佳客户将您目录中所有衣服的折扣降低50%。

此报价针对的是您美国商店的最佳客户，即自年初以来已花费超过300美元的客户。

因此，您决定使用“分布式营销”来创建协作式营销活动（通过目标批准），这允许您选择您商店的最佳客户（按区域分组），这些客户将收到包含特价优惠的电子邮件分发。

此示例的第一部分说明了接收营销活动创建通知的本地实体，以及他们如何使用该通知评估营销活动并对其进行排序。

此示例的第二部分介绍如何创建营销活动。

步骤如下：

**对于本地实体**

1. 使用营销活动创建通知可访问由中央实体选择的联系人列表。
1. 选择联系人并批准参与。

**对于中央实体：**

1. 创建活 **[!UICONTROL Data distribution]** 动。
1. 创建协作营销活动。
1. 发布营销活动。

### 本地实体端 {#local-entity-side}

1. 已选择参加营销活动的本地实体将收到电子邮件通知。

   ![](assets/mkg_dist_use_case_target_valid8.png)

1. 通过单击链 **[!UICONTROL Access your contact list and approve targeting]** 接，本地实体可（通过Web浏览器）访问为营销活动选择的客户端列表。

   ![](assets/mkg_dist_use_case_target_valid9.png)

1. 当地实体从列表中取消检查某些联系人，因为自年初以来，他们已联系到他们寻求类似报价。

   ![](assets/mkg_dist_use_case_target_valid10.png)

检查获得批准后，营销活动可以自动启动。

### 中央实体侧 {#central-entity-side}

#### 创建数据分发活动 {#creating-a-data-distribution-activity}

1. 要设置协作式营销活动（通过目标批准），您必须先创建 **[!UICONTROL Data distribution activity]**。 单击节 **[!UICONTROL New]** 点中的图 **[!UICONTROL Resources > Campaign management > Data distribution]** 标。

   ![](assets/mkg_dist_use_case_target_valid3.png)

1. 在选项卡 **[!UICONTROL General]** 中，您必须指定：

   * the **[!UICONTROL Targeting dimension]** the. 此处 **在收件人** 上执行数据 **分发**。
   * the **[!UICONTROL Distribution type]** the. 您可以选择固定 **大小** ，或 **大小作为百分比**。
   * the **[!UICONTROL Assignment type]** the. 选择“本 **地实体** ”选项。
   * the **[!UICONTROL Distribution type]** the. 此处是“收件人 **[!UICONTROL Origin (@origin)]** ”表中显示的字段，用于识别联系人与本地实体之间的关系。
   * 字 **[!UICONTROL Approval storage]** 段。 选择“接收 **者的本地批准** ”选项。

1. 在选项卡 **[!UICONTROL Breakdown]** 中，指定：

   * 它 **[!UICONTROL Distribution field value]**&#x200B;对应于参与即将开展的营销活动的本地实体。
   * 本地实体 **[!UICONTROL label]**。
   * ( **[!UICONTROL Size]** 固定或百分比)。 默认 **值为** 0，包括选择链接到本地实体的所有收件人。
   ![](assets/mkg_dist_use_case_target_valid4.png)

1. 保存新的数据分发。

#### 创建协作营销活动 {#creating-a-collaborative-campaign}

1. 从节 **[!UICONTROL Campaign management > Campaign]** 点创建新 **[!UICONTROL collaborative campaign (by target approval)]**。
1. 在选项卡中， **[!UICONTROL Targeting and workflows]** 为您的营销活动创建一个工作流。 它必须包含 **Split** （拆分）活动，活动 **[!UICONTROL Record count limitation]** 在其中定义该 **[!UICONTROL Data distribution]** 活动。

   ![](assets/mkg_dist_use_case_target_valid5.png)

1. 添加一 **[!UICONTROL Local approval]** 个可指定的操作：

   * 发送给通知中的本地实体的消息内容，
   * 批准提醒，
   * 营销活动的预期处理
   ![](assets/mkg_dist_use_case_target_valid7.png)

1. 保存记录。

#### 发布营销活动 {#publishing-the-campaign}

您现在可以从“营销活 **动”范围中** ，添加 **营销活动包** 。

1. 选择您的 **[!UICONTROL Reference campaign]**。 在包的 **[!UICONTROL Edit]** 选项卡中，您可以选择要用 **[!UICONTROL Approval mode]** 于营销活动的选项：

   * 在“ **手动** ”模式中，如果本地实体接受来自中央实体的邀请，则它们会参与营销活动。 如果他们想要删除预选的联系人，并且需要经理的批准才能确认其参与营销活动，他们可以删除这些联系人。
   * 在自 **动模式下** ，本地实体必须参与营销活动，除非它们从中取消注册。 他们无需批准即可删除联系人。
   ![](assets/mkg_dist_use_case_target_valid.png)

1. 在该选 **[!UICONTROL Description]** 项卡中，您可以为营销活动以及要发送到本地实体的任何文档添加说明。

   ![](assets/mkg_dist_use_case_target_valid1.png)

1. 批准您的营销活动包，然后启动发布包的工作流，并将其发布到包列表中的所有本地实体。

   ![](assets/mkg_dist_use_case_target_valid2.png)

## 创建协作式营销活动（按表单） {#creating-a-collaborative-campaign--by-form-}

### 简介 {#introduction-1}

您是一家大型化妆品品牌的营销经理，该品牌在美国各地拥有一家网上商店和几家精品店。 要卸载冬季库存并为新库存腾出空间，您决定创建一个特价优惠，该优惠针对两个客户类别：30岁以上的人，你将为他们提供年龄敏感的护肤产品，30岁以下的人，你将为他们提供更基本的护肤产品。

因此，您决定使用“分布式营销”创建协作式营销活动（按表单），以便您能够根据年龄范围从不同商店中选择客户。 这些客户将收到一封电子邮件，其中附有根据年龄范围个性化的特价优惠。

此示例的第一部分说明了接收营销活动创建通知的本地实体，以及他们如何使用该通知评估营销活动并对其进行排序。

此示例的第二部分介绍如何创建营销活动。

步骤如下：

**对于本地实体**

1. 使用营销活动创建通知访问在线表单。
1. 个性化营销活动（目标、内容、投放量）。
1. 检查这些字段，并根据需要更改它们。
1. 批准您的参与。
1. 本地实体（或中央实体）的经理批准您的配置和参与。

**对于中央实体：**

1. 创建协作营销活动。
1. 像配置 **[!UICONTROL Advanced campaign settings...]** 本地营销活动一样配置。
1. 像配置本地营销活动一样配置营销活动工作流和分发。
1. 更新Web表单。
1. 创建营销活动包并发布它。

### 本地实体端 {#local-entity-side-1}

1. 选择参加营销活动的本地实体会收到电子邮件通知，通知他们参与营销活动。

   ![](assets/mkg_dist_use_case_form_7.png)

1. 当地实体填写了个性化表单，然后：

   * 评估目标和预算，
   * 预览交付内容，
   * 批准其参与。

      ![](assets/mkg_dist_use_case_form_8.png)

1. 负责验证订单的运营商批准其参与。

   ![](assets/mkg_dist_use_case_form_9.png)

### 中央实体侧 {#central-entity-side-1}

1. 要实施协作式营销活动（按表单），您必须使用协作式营销活动(按表 **单)模板创建营销活动** 。

   ![](assets/mkg_dist_use_case_form_1.png)

1. 在营销活动的选 **[!UICONTROL Edit]** 项卡中，单击链 **[!UICONTROL Advanced campaign settings...]** 接以将其配置为本地营销活动。 请参阅 [创建本地营销活动（按表单）](#creating-a-local-campaign--by-form-)。

   ![](assets/mkg_dist_use_case_form_2.png)

1. 配置营销活动工作流和Web表单。 请参阅 [创建本地营销活动（按表单）](#creating-a-local-campaign--by-form-)。
1. 通过指定执行计划和涉及的本地实体，创建您的系列活动包。

   ![](assets/mkg_dist_use_case_form_3.png)

1. 通过在选项卡中选择批准模式来完成包配 **[!UICONTROL Edit]** 置。

   ![](assets/mkg_dist_use_case_form_4.png)

1. 在该选 **[!UICONTROL Description]** 项卡中，您可以输入营销活动包描述，在发布包时向本地实体发送通知消息，并将任何信息性文档附加到营销活动包。

   ![](assets/mkg_dist_use_case_form_5.png)

1. 批准包以发布它。

   ![](assets/mkg_dist_use_case_form_6.png)

