---
solution: Campaign Classic
product: campaign
title: 具有自定义日期字段的电子邮件扩充
description: 了解如何使用自定义日期字段丰富电子邮件
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 3%

---


# 具有自定义日期字段的电子邮件扩充{#email-enrichment-with-custom-date-fields}

在此示例中，我们希望向本月庆祝生日的收件人发送一封包含自定义数据字段的电子邮件。 该电子邮件将包含一个优惠券，其有效期为生日前后一周。

我们需要目标列表的收件人，他们本月将用&#x200B;**[!UICONTROL Split]**&#x200B;活动庆祝生日。 然后，使用&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动，自定义数据字段将作为客户特殊优惠的电子邮件的有效日期。

![](assets/uc_enrichment.png)

要创建此示例，请应用以下步骤：

1. 在活动的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;选项卡中，拖放&#x200B;**[!UICONTROL Read list]**&#x200B;活动以目标列表收件人。
1. 要处理的列表可以显式指定，由脚本计算，也可以根据此处选择的选项和定义的参数动态本地化。

   ![](assets/uc_enrichment_1.png)

1. 添加&#x200B;**[!UICONTROL Split]**&#x200B;活动，区分本月将庆祝生日的收件人与其他收件人。
1. 要拆分列表，请在&#x200B;**[!UICONTROL Filtering of selected records]**&#x200B;类别中，选择&#x200B;**[!UICONTROL Add a filtering condition on the inbound population]**。 然后，单击&#x200B;**[!UICONTROL Edit]**。

   ![](assets/uc_enrichment_2.png)

1. 选择&#x200B;**[!UICONTROL Filtering conditions]**，然后单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;按钮以过滤收件人生日的月份。

   ![](assets/uc_enrichment_3.png)

1. 单击&#x200B;**[!UICONTROL Advanced Selection]**，然后单击&#x200B;**[!UICONTROL Edit the formula using an expression]**&#x200B;并添加以下表达式:Month(@birthDate)。
1. 在&#x200B;**[!UICONTROL Operator]**&#x200B;列中，选择&#x200B;**[!UICONTROL equal to]**。
1. 通过添加当前日期的&#x200B;**[!UICONTROL Value]**&#x200B;月，进一步过滤您的条件：Month(GetDate())。

   这将查询生日月份与当月相对应的收件人。

   ![](assets/uc_enrichment_4.png)

1. 单击 **[!UICONTROL Finish]**。然后，在&#x200B;**[!UICONTROL Split]**&#x200B;活动的&#x200B;**[!UICONTROL General]**&#x200B;选项卡中，单击&#x200B;**[!UICONTROL Results]**&#x200B;类别中的&#x200B;**[!UICONTROL Generate complement]**。

   使用&#x200B;**[!UICONTROL Complement]**&#x200B;结果，您可以添加投放活动或更新列表。 这里，我们刚刚添加了&#x200B;**[!UICONTROL End]**&#x200B;活动。

   ![](assets/uc_enrichment_6.png)

您现在需要配置&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动:

1. 在子集后添加&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动，以添加自定义日期字段。

   ![](assets/uc_enrichment_7.png)

1. 打开&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动。 在&#x200B;**[!UICONTROL Complementary information]**&#x200B;类别中，单击&#x200B;**[!UICONTROL Add data]**。

   ![](assets/uc_enrichment_8.png)

1. 选择&#x200B;**[!UICONTROL Data linked to the filtering dimension]**，然后选择&#x200B;**[!UICONTROL Data of the filtering dimension]**。
1. 单击 **[!UICONTROL Add]** 按钮。

   ![](assets/uc_enrichment_9.png)

1. 添加&#x200B;**[!UICONTROL Label]**。 然后，在&#x200B;**[!UICONTROL Expression]**&#x200B;列中，单击&#x200B;**[!UICONTROL Edit expression]**。

   ![](assets/uc_enrichment_10.png)

1. 首先，我们需要将出生日期前的一周目标为&#x200B;**有效开始日期**，并使用以下&#x200B;**[!UICONTROL Expression]**:`SubDays([target/@birthDate], 7)`。

   ![](assets/uc_enrichment_11.png)

1. 然后，要创建自定义日期字段&#x200B;**Validity end date**(将目标出生日期后的一周)，您需要添加&#x200B;**[!UICONTROL Expression]**:`AddDays([target/@birthDate], 7)`。

   您可以向表达式添加标签。

   ![](assets/uc_enrichment_12.png)

1. 单击 **[!UICONTROL Ok]**。您的扩充已准备就绪。

在&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动后，可以添加投放。 在这种情况下，我们添加了电子邮件投放，以向收件人发送具有有效日期的特殊优惠，以便客户在本月庆祝他们的生日。

1. 在&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动之后拖放&#x200B;**[!UICONTROL Email delivery]**&#x200B;活动。

   ![](assets/uc_enrichment_15.png)

1. 多次-单击您的&#x200B;**[!UICONTROL Email delivery]**&#x200B;活动,开始个性化投放。
1. 将&#x200B;**[!UICONTROL Label]**&#x200B;添加到投放，然后单击&#x200B;**[!UICONTROL Continue]**。
1. 单击&#x200B;**[!UICONTROL Save]**&#x200B;以创建电子邮件投放。
1. 检查电子邮件投放&#x200B;**[!UICONTROL Properties]**&#x200B;的&#x200B;**[!UICONTROL Approval]**&#x200B;选项卡，确认已检查&#x200B;**[!UICONTROL Confirm delivery before sending option]**。

   然后，开始您的工作流，以利用目标信息丰富您的出站过渡。

   ![](assets/uc_enrichment_18.png)

您现在可以开始设计电子邮件投放，使用在&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动中创建的自定义日期字段。

1. 多次-单击&#x200B;**[!UICONTROL Email delivery]**&#x200B;活动。
1. 将目标扩展添加到电子邮件中。 它应位于以下表达式中，以配置有效日期的格式：

   ```
   <%=
           formatDate(targetData.alias of your expression,"%2D.%2M")  %>
   ```

1. 单击 ![](assets/uc_enrichment_16.png)。选择&#x200B;**[!UICONTROL Target extension]**，然后选择之前创建的具有&#x200B;**[!UICONTROL Enrichment]**&#x200B;活动的自定义有效性日期，以将您的扩展添加到formatDate表达式。

   ![](assets/uc_enrichment_19.png)

1. 根据需要配置电子邮件内容。

   ![](assets/uc_enrichment_17.png)

1. 预览电子邮件以检查自定义日期字段是否配置正确

   ![](assets/uc_enrichment_20.png)

您的电子邮件现已准备就绪。 您可以开始发送验证并确认投放发送生日电子邮件。
