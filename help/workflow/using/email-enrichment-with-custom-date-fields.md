---
title: 电子邮件丰富了自定义日期字段
seo-title: 电子邮件丰富了自定义日期字段
description: 电子邮件丰富了自定义日期字段
seo-description: null
page-status-flag: never-activated
uuid: 6dd240b1-f995-4e12-90a5-55aeb584bcdc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 9cb3be65-6652-47fa-b8a4-e088530aab4a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c4b5b7c44bbc74f56d3c70b93b131bba4d78c6f

---


# 电子邮件丰富了自定义日期字段{#email-enrichment-with-custom-date-fields}

在此示例中，我们希望向本月将庆祝生日的收件人发送一封包含自定义数据字段的电子邮件。 电子邮件中将包含一个优惠券，其有效期为一周，为生日前后。

我们需要从一个列表中定位收件人，这些收件人将在本月庆祝生日并参加 **[!UICONTROL Split]** 活动。 然后，使用活 **[!UICONTROL Enrichment]** 动，自定义数据字段将作为客户特价优惠电子邮件的有效日期。

![](assets/uc_enrichment.png)

要创建此示例，请应用以下步骤：

1. 在营销 **[!UICONTROL Targeting and workflows]** 活动的选项卡中，拖放活动以 **[!UICONTROL Read list]** 定位收件人列表。
1. 要处理的列表可以显式指定，由脚本计算，或根据此处选择的选项和定义的参数动态本地化。

   ![](assets/uc_enrichment_1.png)

1. 添加活 **[!UICONTROL Split]** 动，以区分本月将庆祝生日的收件人与其他收件人。
1. 要拆分列表，请在类别 **[!UICONTROL Filtering of selected records]** 中选择 **[!UICONTROL Add a filtering condition on the inbound population]**。 然后，单击 **[!UICONTROL Edit]**。

   ![](assets/uc_enrichment_2.png)

1. 选 **[!UICONTROL Filtering conditions]** 择，然后单 **[!UICONTROL Edit expression]** 击按钮以过滤收件人生日的月份。

   ![](assets/uc_enrichment_3.png)

1. 单击 **[!UICONTROL Advanced Selection]** 然后 **[!UICONTROL Edit the formula using an expression]** 添加以下表达式：Month(@birthDate)。
1. 在列 **[!UICONTROL Operator]** 中，选择 **[!UICONTROL equal to]**。
1. 通过添加当前日期的月份，进 **[!UICONTROL Value]** 一步过滤您的条件：Month(GetDate())。

   这将查询其生日月份与当月对应的收件人。

   ![](assets/uc_enrichment_4.png)

1. 单击 **[!UICONTROL Finish]**. 然后，在活动 **[!UICONTROL General]** 的选项卡 **[!UICONTROL Split]** 中，单击类 **[!UICONTROL Generate complement]** 别中的 **[!UICONTROL Results]** 选项卡。

   结果 **[!UICONTROL Complement]** 是，您可以添加交付活动或更新列表。 我们刚刚在此添加了一个 **[!UICONTROL End]** 活动。

   ![](assets/uc_enrichment_6.png)

您现在需要配置活 **[!UICONTROL Enrichment]** 动：

1. 在子集之 **[!UICONTROL Enrichment]** 后添加活动，以添加自定义日期字段。

   ![](assets/uc_enrichment_7.png)

1. 打开您的 **[!UICONTROL Enrichment]** 活动。 在类 **[!UICONTROL Complementary information]** 别中，单击 **[!UICONTROL Add data]**。

   ![](assets/uc_enrichment_8.png)

1. 然后 **[!UICONTROL Data linked to the filtering dimension]** 选择 **[!UICONTROL Data of the filtering dimension]**。
1. Click the **[!UICONTROL Add]** button.

   ![](assets/uc_enrichment_9.png)

1. 添加 **[!UICONTROL Label]**。 然后，在列 **[!UICONTROL Expression]** 中单击 **[!UICONTROL Edit expression]**。

   ![](assets/uc_enrichment_10.png)

1. 首先，我们需要将出生日期前一周作为有效 **性开始日期** ，具体如下 **[!UICONTROL Expression]**: `SubDays([target/@birthDate], 7)`.

   ![](assets/uc_enrichment_11.png)

1. 然后，要创建定制日期字段 **有效性结束日期** （该字段将定位于出生日期后的一周），您需要添加 **[!UICONTROL Expression]**: `AddDays([target/@birthDate], 7)`.

   您可以向表达式添加标签。

   ![](assets/uc_enrichment_12.png)

1. 单击 **[!UICONTROL Ok]**. 你的丰富现已就绪。

活动 **[!UICONTROL Enrichment]** 完成后，您可以添加分发。 在这种情况下，我们添加了一封电子邮件，以向收件人发送一份特惠，其有效期为本月过生日的客户。

1. 在活动后拖 **[!UICONTROL Email delivery]** 放活 **[!UICONTROL Enrichment]** 动。

   ![](assets/uc_enrichment_15.png)

1. 双击活动以开 **[!UICONTROL Email delivery]** 始个性化交付。
1. 在您的 **[!UICONTROL Label]** 分发中添加并单击 **[!UICONTROL Continue]**。
1. 单击 **[!UICONTROL Save]** 以创建电子邮件分发。
1. 签入已选 **[!UICONTROL Approval]** 中的电子邮件分 **[!UICONTROL Properties]** 发的 **[!UICONTROL Confirm delivery before sending option]** 选项卡。

   然后，启动您的工作流，以利用目标信息丰富您的出站过渡。

   ![](assets/uc_enrichment_18.png)

您现在可以开始设计电子邮件分发，其中包含在活动中创建的自定义日期 **[!UICONTROL Enrichment]** 字段。

1. 双击您的活 **[!UICONTROL Email delivery]** 动。
1. 将目标扩展添加到电子邮件中。 它应位于以下表达式中，以配置有效日期的格式：

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. 单击 ![](assets/uc_enrichment_16.png) . 选 **[!UICONTROL Target extension]** 择之前创建的自定义有效性日期以及活 **[!UICONTROL Enrichment]** 动，将您的扩展添加到formatDate表达式。

   ![](assets/uc_enrichment_19.png)

1. 根据需要配置电子邮件内容。

   ![](assets/uc_enrichment_17.png)

1. 预览电子邮件以检查自定义日期字段是否配置正确

   ![](assets/uc_enrichment_20.png)

您的电子邮件现已准备就绪。 您可以开始发送校样并确认您的送达方式以发送生日电子邮件。
