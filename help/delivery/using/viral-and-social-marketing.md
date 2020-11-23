---
solution: Campaign Classic
product: campaign
title: 病毒式和社交媒体营销
description: 病毒式和社交媒体营销
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 2%

---


# 病毒式和社交媒体营销{#viral-and-social-marketing}

## 关于病毒式营销 {#about-viral-marketing}

Adobe Campaign可让您设置各种工具来鼓励病毒式营销。

这样，投放收件人或网站访客可以与其网络共享信息：从添加指向其Facebook或Twitter用户档案的链接到向朋友发送消息。

![](assets/s_ncs_user_viral_icons.png)

>[!CAUTION]
>
>要使添加的链接正常工作，必须提供匹配镜像页面。 为此，请在投放中包含指向镜像页面的链接。

## 社交网络：共享链接 {#social-networks--sharing-a-link}

要使投放收件人能够与其网络成员共享消息内容，您需要包含匹配的个性化块。

![](assets/s_ncs_user_viral_add_link.png)

>[!NOTE]
>
>默认情况下，此链接在块列表中不提供。 您可以通过单击并选 **[!UICONTROL Other...]**&#x200B;择块来访问 **[!UICONTROL Social network sharing links]** 它。

![](assets/s_ncs_user_viral_add_link_via_others.png)

渲染将如下所示：

![](assets/s_ncs_user_viral_add_link_rendering.png)

当收件人单击显示的某个社交网络的图标时，他们会自动重定向到其帐户，并可通过链接共享消息内容。 这允许其网络成员访问通信。

>[!NOTE]
>
>此个性化块包含所有链接（用于与所有社交网络发送和共享消息）。 可以根据您的需求进行更改。 但是，配置是为高级用户保留的。 要编辑匹配的个性化块，请转 **[!UICONTROL Resources > Campaign management > Personalization blocks]** 到Adobe Campaign树的节点。

## 病毒式营销：向朋友转达 {#viral-marketing--forward-to-a-friend}

传播服务允许执行引用类型操作：这些操作使您能够将消息转发给朋友。 用户档案的被推荐人临时存储在数据库中（在专用表中）。 转发的消息包括被推荐人订阅的链接：如果他们这样做，他们将添加到Adobe Campaign库。

消息转发与社交网络链路的原理相同。

应用以下阶段：

1. 将个性化 **[!UICONTROL Social network sharing links]** 块添加到原始消息的正文中。
1. 消息收件人可以单击 **[!UICONTROL Email]** 该图标将此消息发送给一个或多个朋友。

   ![](assets/s_ncs_user_viral_email_link.png)

   通过引用表单，您可以输入被推荐人的电子邮件地址。

   ![](assets/s_ncs_user_viral_email_msg.png)

   当主收件人单击该按钮时，消息将发送给 **[!UICONTROL Next]** 他们。

   >[!NOTE]
   >
   >此消息的内容可以个性化以满足您的需求。 它根据存储在节 **[!UICONTROL Transfer of original message]** 点中的模板创建 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 。
   >
   >还可以更改推荐人可用的消息转发表单。为此，您需要更改存储在节 **点中的** “病毒”表单 **[!UICONTROL Resources > Online > Web applications]** Web 应用程序。

1. 在转发的消息中，有一个链接允许被推荐人将其用户档案保存在数据库中。 为此提供了条目表单。

   ![](assets/s_ncs_user_viral_create_account_form.png)

   >[!NOTE]
   >
   >此配置可以调整。 为此，您需要修改存储在节 **点中的收件人** 订阅 **[!UICONTROL Resources > Online > Web applications]** Web 应用程序。
   >
   >For more information on Web applications, refer to [this section](../../web/using/about-web-applications.md).

   验证后，系统会向他们发送确认消息：只有在他们激活确认消息中的链接后，他们才会永久注册。 此消息是根据存储在 **[!UICONTROL Registration confirmation]** 节点中的模板创建 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 的。

   该被推荐人将添加到 **** 库的收件人文件夹，并订阅（默认情况下）新闻快 **讯** 信息服务。

## 跟踪社交网络共享 {#tracking-social-network-sharing}

跟踪共享信息和对共享信息的访问。 由Adobe Campaign收集的此信息可在以下两个位置访问：

* 在投放 **[!UICONTROL Tracking]** 的选项卡中(或针对每个收件人单独进行):

   ![](assets/s_ncs_user_network_del_tracking_tab.png)

* 在专门的报 **[!UICONTROL Sharing to social networks]** 告中：

   ![](assets/s_ncs_user_viral_report.png)

