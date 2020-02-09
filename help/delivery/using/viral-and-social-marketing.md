---
title: 病毒式和社交营销
seo-title: 病毒式和社交营销
description: 病毒式和社交营销
seo-description: null
page-status-flag: never-activated
uuid: dca3db7e-cc8d-42ca-b1b8-45e9fb739c97
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
discoiquuid: 66f2b229-92d9-4db1-97a4-2d9eb2270446
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 病毒式和社交营销{#viral-and-social-marketing}

## 关于病毒式营销 {#about-viral-marketing}

Adobe Campaign可让您设置各种工具来鼓励病毒式营销。

这样，交付收件人或网站访问者就可以与其网络共享信息：从添加指向其Facebook或Twitter个人资料的链接到向朋友发送消息。

![](assets/s_ncs_user_viral_icons.png)

>[!CAUTION]
>
>要使添加的链接正常工作，必须提供匹配的镜像页面。 为此，请在分发中包含指向镜像页面的链接。

## 社交网络：共享链接 {#social-networks--sharing-a-link}

要使交付收件人能够与其网络成员共享消息内容，您需要包含匹配的个性化块。

![](assets/s_ncs_user_viral_add_link.png)

>[!NOTE]
>
>默认情况下，块列表中不提供此链接。 您可以通过单击并选 **[!UICONTROL Other...]**&#x200B;择块来访问 **[!UICONTROL Social network sharing links]** 它。

![](assets/s_ncs_user_viral_add_link_via_others.png)

渲染将如下所示：

![](assets/s_ncs_user_viral_add_link_rendering.png)

当收件人单击显示的某个社交网络的图标时，他们会自动被重定向到自己的帐户，并可以通过链接共享消息内容。 这使其网络成员可以访问通信。

>[!NOTE]
>
>此个性化块包含所有链接（用于与所有社交网络发送和共享消息）。 可以根据您的需求进行更改。 但是，配置是为高级用户保留的。 要编辑匹配的个性化块，请转 **[!UICONTROL Resources > Campaign management > Personalization blocks]** 到Adobe Campaign树的节点。

## 病毒式营销：向朋友转达 {#viral-marketing--forward-to-a-friend}

病毒式服务允许执行引用类型的操作：这些操作使您能够将消息转发给朋友。 裁判者的档案被临时存储在数据库中（在专用表中）。 转发的消息包括一个供裁判订阅的链接：如果他们这样做，他们将被添加到Adobe Campaign数据库。

消息转发与社交网络链接的原理相同。

应用以下阶段：

1. 将个性 **[!UICONTROL Social network sharing links]** 化块添加到原始消息的正文中。
1. 邮件收件人可以单击该 **[!UICONTROL Email]** 图标以将此邮件发送给一个或多个朋友。

   ![](assets/s_ncs_user_viral_email_link.png)

   通过推荐表单，您可以输入裁判的电子邮件地址。

   ![](assets/s_ncs_user_viral_email_msg.png)

   当主收件人单击该按钮时，消息会发送给 **[!UICONTROL Next]** 他们。

   >[!NOTE]
   >
   >此消息的内容可以个性化以满足您的需求。 它基于存储在节 **[!UICONTROL Transfer of original message]** 点中的模板创建 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 的。
   >
   >还可以更改向引用者提供的消息转发表单。要执行此操作，您需要更改存储在节点中的 **Viral form** web应用程 **[!UICONTROL Resources > Online > Web applications]** 序。

1. 在转发的消息中，链接允许裁判将他们的档案保存在数据库中。 为此，提供了一个条目表单。

   ![](assets/s_ncs_user_viral_create_account_form.png)

   >[!NOTE]
   >
   >这种配置可以调整。 为此，您需要修改存储在节 **点中的Recipient** Subscription web应用 **[!UICONTROL Resources > Online > Web applications]** 程序。
   >
   >For more information on Web applications, refer to [this section](../../web/using/about-web-applications.md).

   验证后，系统会向他们发送确认消息：只有在激活确认消息中的链接后，才会永久注册这些用户。 此消息基于存储在节 **[!UICONTROL Registration confirmation]** 点中的模板而创 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 建。

   裁判将添加到数据库的 **Recipients** 文件夹，并订阅（默认情况下） **Newsletter** 信息服务。

## 跟踪社交网络共享 {#tracking-social-network-sharing}

跟踪共享信息和对共享信息的访问。 Adobe Campaign收集的此信息可在以下两个位置访问：

* 在分发 **[!UICONTROL Tracking]** 的选项卡中（或针对每个收件人单独显示）:

   ![](assets/s_ncs_user_network_del_tracking_tab.png)

* 在专门报告 **[!UICONTROL Sharing to social networks]** 中：

   ![](assets/s_ncs_user_viral_report.png)

