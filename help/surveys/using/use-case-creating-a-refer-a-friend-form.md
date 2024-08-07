---
product: campaign
title: 创建“推荐朋友”调查
description: 了解创建“推荐朋友”表单的步骤
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Surveys
exl-id: bd94c41a-813a-4ddb-a2bd-c3deab022482
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 0%

---

# 用例：创建引用窗体{#use-case-creating-a-refer-a-friend-form}



在本例中，我们希望向数据库中的收件人提供一个竞争对手。 在Web窗体中，有一个部分用于输入答案，另一个部分用于通过输入朋友的电子邮件地址来介绍朋友。

![](assets/s_ncs_admin_survey_viral_sample_0.png)

使用前面描述的过程创建识别块和竞争块。

要配置和创建反向链接块，请应用以下步骤：

1. 创建竞争Web表单，其中包含各种问题和用于输入朋友联系信息的字段，如下所示：

   ![](assets/s_ncs_admin_survey_viral_sample_2.png)

   **您的消息**&#x200B;字段允许您为被推荐人输入消息。 反向链接还必须输入其&#x200B;**姓氏**、**名字**&#x200B;和&#x200B;**电子邮件**。

   在字段中输入的信息存储在称为访客表的特定表中。

   >[!NOTE]
   >
   >只要收件人未表示同意，您就不能将它们与收件人一起存储在数据库中。 它们将临时存储在为病毒式营销活动设计的&#x200B;**访客**&#x200B;表(**nms：visitor**)中。 由于&#x200B;**清理**&#x200B;操作，将定期清除此表。
   >
   >在本例中，我们要定位收件人，以建议他们参加其反向链接所推荐的竞争。 但是，在本邮件中，我们还希望向他们提供我们的一个信息服务的订购。 如果它们订阅，则它们可以存储在数据库中。

   ![](assets/s_ncs_admin_survey_viral_sample_5.png)

   与被推荐人相关的字段内容将在用户档案创建脚本和发送给他们的消息中使用。

1. 首先，创建脚本以将反向链接链接到被推荐人。

   它包含以下说明：

   ![](assets/s_ncs_admin_survey_viral_sample_4.png)

   ```
   ctx.recipient.visitor.@id = xtk.session.GetNewIds(1)
   ctx.recipient.visitor.@forwardUrl = "APP5"
   ctx.recipient.visitor.@referrerEmail = ctx.recipient.@email
   ctx.recipient.visitor.@referrerFirstName = ctx.recipient.@firstName
   ctx.recipient.visitor.@referrerLastName = ctx.recipient.@lastName
   ```

   在页面标识块中输入的姓氏、名字和电子邮件地址被标识为反向链接姓氏、名字和电子邮件地址。 这些字段将重新插入到发送给裁判的消息正文中。

   APP5值与Web窗体的内部名称匹配：利用此信息，可了解被推荐人的来源，即将访客链接到基于其创建的Web窗体。

1. 利用存储框，您可以收集信息并将其存储在数据库中。

   ![](assets/s_ncs_admin_survey_viral_sample_4b.png)

1. 然后，创建链接到在步骤1中创建的信息服务的投放模板。 它将在信息服务的&#x200B;**[!UICONTROL Choose scenario]**&#x200B;字段中选择。

   用于创建反向链接选件消息的投放模板包含以下信息：

   ![](assets/s_ncs_admin_survey_viral_sample_7.png)

   此模板具有以下特性：

   * 选择访客表作为目标映射。

     ![](assets/s_ncs_admin_survey_viral_sample_7b.png)

   * 被推荐人的联系信息以及有关反向链接的信息均取自访客表。 可使用个性化按钮插入内容。

     ![](assets/s_ncs_admin_survey_viral_sample_7a.png)

   * 此模板包含竞争表格和订阅链接的链接，供被推荐人订阅新闻稿。

     通过个性化块插入订阅链接。 默认情况下，它允许您订阅用户档案到&#x200B;**新闻稿**&#x200B;服务。 可以根据您的需要更改此个性化块，例如，为收件人订阅其他服务。

   * 内部名称（此处为“referrer”）将在消息投放脚本中使用，如下所示。

   >[!NOTE]
   >
   >有关投放模板的详细信息，请参阅[此页面](../../delivery/using/about-templates.md)。

1. 创建用于投放订阅消息的第二个脚本。

   ![](assets/s_ncs_admin_survey_viral_sample_7c.png)

   ```
   // Updtate visitor to have a link to the referrer recipient
   ctx.recipient.visitor.@referrerId = ctx.recipient.@id
   ctx.recipient.visitor.@xtkschema = "nms:visitor"
   ctx.recipient.visitor.@_operation = "update" 
   ctx.recipient.visitor.@_key = "@id" 
   xtk.session.Write(ctx.recipient.visitor)
   
   // Send email to friend
   nms.delivery.QueueNotification("referrer",
   <delivery>
   <targets>
     <deliveryTarget>
       <targetPart type='query' exclusion='false' ignoreDeleteStatus='false'>
         <where>
           <condition expr={'@id IN ('+ ctx.recipient.visitor.@id +')' }/>
         </where>
       </targetPart>
      </deliveryTarget>
     </targets>
    </delivery>)
   ```

1. Publish竞争表，并向初始目标的收件人发送邀请。 当其中一个邀请朋友时，将创建基于&#x200B;**反向链接选件**&#x200B;模板的投放。

   ![](assets/s_ncs_admin_survey_viral_sample_8.png)

   被推荐人已添加到&#x200B;**[!UICONTROL Administration > Visitors node]**&#x200B;中的访客文件夹：

   ![](assets/s_ncs_admin_survey_viral_sample_9.png)

   其个人资料包含其反向链接输入的信息。 它基于在表单脚本中输入的配置进行存储。 如果他们决定订阅新闻稿，将保存在收件人表中。
