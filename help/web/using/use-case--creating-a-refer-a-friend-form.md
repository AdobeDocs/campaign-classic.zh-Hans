---
title: “用例：创建“参考朋友”表单
seo-title: “用例：创建“参考朋友”表单
description: “用例：创建“参考朋友”表单
seo-description: null
page-status-flag: never-activated
uuid: ad8b9076-c551-420d-bb23-0b3c645ee943
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: bbb1154f-2818-489c-9860-0e860596cbf7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# 用例：创建“参考朋友”表单{#use-case-creating-a-refer-a-friend-form}

在此示例中，我们希望向数据库中的收件人提供竞赛。 Web表单将包含一个用于输入答案的部分，另一个用于通过输入朋友的电子邮件地址来引用朋友。

![](assets/s_ncs_admin_survey_viral_sample_0.png)

识别和竞争块是使用前面描述的过程创建的。

要配置和创建引用块，请应用以下步骤：

1. 创建包含问题的竞赛Web表单，并创建一个用于输入朋友的联系信息的字段，如下所示：

   ![](assets/s_ncs_admin_survey_viral_sample_2.png)

   在“ **您的消息** ”字段中，您可以输入裁判的消息。 引用网站还必须输入其姓 **氏**、名 **字和电子** 邮件 ****。

   在字段中输入的信息存储在称为访客表的特定表中。

   >[!NOTE]
   >
   >只要收件人未征得其同意，您就不能将其存储在数据库中。 它们将临时存储在访客表 **格** (**nms:visitor**)中，该表格专为病毒式营销活动而设计。 由于进行了清理操作，此表会定期 **清除** 。
   >
   >在此示例中，我们希望目标收件人建议他们参加其引用网站推荐的竞赛。 但是，在此消息中，我们还希望为他们订阅我们的一项信息服务。 如果订阅，则可以将其存储在数据库中。

   ![](assets/s_ncs_admin_survey_viral_sample_5.png)

   将在档案创建脚本和发送给裁判的消息中使用与裁判有关的字段的内容。

1. 首先创建一个脚本，将参照者与裁判联系起来。

   它包含以下说明：

   ![](assets/s_ncs_admin_survey_viral_sample_4.png)

   ```
   ctx.recipient.visitor.@id = xtk.session.GetNewIds(1)
   ctx.recipient.visitor.@forwardUrl = "APP5"
   ctx.recipient.visitor.@referrerEmail = ctx.recipient.@email
   ctx.recipient.visitor.@referrerFirstName = ctx.recipient.@firstName
   ctx.recipient.visitor.@referrerLastName = ctx.recipient.@lastName
   ```

   在页面标识块中输入的姓氏、名字和电子邮件地址标识为引介的姓氏、名字和电子邮件地址。 这些田地将重新注入发给裁判的信件中。

   APP5值与Web表单的内部名称相匹配：此信息可让您查明裁判的来源，即将访客关联到基于其创建的Web表单。

1. 通过存储框，您可以收集信息并将其存储在数据库中。

   ![](assets/s_ncs_admin_survey_viral_sample_4b.png)

1. 然后，创建链接到在步骤1中创建的信息服务的分发模板。 将在信息服务的 **[!UICONTROL Choose scenario]** 字段中选择它。

   用于创建引用选件消息的交付模板包含以下信息：

   ![](assets/s_ncs_admin_survey_viral_sample_7.png)

   此模板具有以下特点：

   * 选择访客表作为目标映射。

      ![](assets/s_ncs_admin_survey_viral_sample_7b.png)

   * 裁判的联系信息以及参照者的信息从访客表中获取。 它使用个性化按钮插入。

      ![](assets/s_ncs_admin_survey_viral_sample_7a.png)

   * 此模板包含一个指向竞赛表单的链接以及裁判订阅新闻稿的订阅链接。

      通过个性化块插入订阅链接。 默认情况下，它允许您将配置文件订阅到 **Newsletter** 服务。 可以根据您的需要更改此个性化块，例如，将收件人订阅到其他服务。

   * 内部名称（此处为“referrer”）将用于消息传送脚本，如下所示。
   >[!NOTE]
   >
   >有关交 [付模板的详细信息](../../delivery/using/about-templates.md) ，请参阅本页。

1. 创建用于传送订阅消息的第二个脚本。

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

1. 发布竞赛表单并向初始目标的收件人发送邀请。 其中一人邀请朋友时，会创建基于推荐选 **件模板的** “分发”。

   ![](assets/s_ncs_admin_survey_viral_sample_8.png)

   裁判将添加到访客文件夹中 **[!UICONTROL Administration > Visitors node]**:

   ![](assets/s_ncs_admin_survey_viral_sample_9.png)

   其配置文件包含其引用网站输入的信息。 它根据在表单脚本中输入的配置进行存储。 如果他们决定订阅新闻稿，则会将其保存在收件人表中。

