---
product: campaign
title: 病毒式营销和社交媒体营销
description: 病毒式营销和社交媒体营销
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 10fd561f-1b07-490e-9f66-d67e44a0def5
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 2%

---

# 病毒式营销和社交媒体营销{#viral-and-social-marketing}



Adobe Campaign允许您设置工具以鼓励病毒式营销。

这样，投放收件人或网站访客就可以与其网络共享信息：从添加指向其Facebook或Twitter用户档案的链接，到向朋友发送消息。

![](assets/s_ncs_user_viral_icons.png)

>[!CAUTION]
>
>为了使添加的链接正常运行，必须提供匹配的镜像页面。 要实现此目的，请在投放中包含指向镜像页面的链接。

## 社交网络：共享链接 {#social-networks--sharing-a-link}

要使投放收件人能够与其网络成员共享消息内容，您需要包含匹配的个性化块。

![](assets/s_ncs_user_viral_add_link.png)

>[!NOTE]
>
>默认情况下，此链接不在块列表中提供。 您可以通过单击 **[!UICONTROL Other...]**，然后选择 **[!UICONTROL Social network sharing links]** 块。

![](assets/s_ncs_user_viral_add_link_via_others.png)

呈现方式如下：

![](assets/s_ncs_user_viral_add_link_rendering.png)

当收件人单击显示的社交网络之一的图标时，他们会自动重定向到其帐户，并可以通过链接共享消息内容。 这样，网络成员就可以访问通信。

>[!NOTE]
>
>此个性化块包含所有链接（用于与所有社交网络发送和共享消息）。 可以根据您的需求进行更改。 但是，配置是为高级用户保留的。 要编辑匹配的个性化块，请转到 **[!UICONTROL Resources > Campaign management > Personalization blocks]** Adobe Campaign树的节点。

## 病毒式营销：转向朋友 {#viral-marketing--forward-to-a-friend}

病毒服务允许执行反向链接类型的操作：这些操作可让您将消息转发给朋友。 推荐人的简介暂时存储在数据库中（在专用表中）。 转发的报文包括供裁判订阅的链接：如果是这样，则会将其添加到Adobe Campaign数据库。

报文转发基于与社交网络链接相同的原则。

应用以下阶段：

1. 添加 **[!UICONTROL Social network sharing links]** 个性化块放入原始消息的正文中。
1. 消息收件人可以单击 **[!UICONTROL Email]** 图标，以将此消息发送给一个或多个朋友。

   ![](assets/s_ncs_user_viral_email_link.png)

   通过推荐表单，您可以输入裁判的电子邮件地址。

   ![](assets/s_ncs_user_viral_email_msg.png)

   当主收件人单击 **[!UICONTROL Next]** 按钮。

   >[!NOTE]
   >
   >此消息的内容可以个性化以满足您的需求。 它基于 **[!UICONTROL Transfer of original message]** 模板，存储在 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 节点。
   >
   >也可以更改提供给反向链接的消息转发表单。要实现此目的，您需要更改 **病毒表单** 存储在 **[!UICONTROL Resources > Online > Web applications]** 节点。

1. 在转发的消息中，链接允许裁判将其个人资料保存在数据库中。 为此目的提供了登入表单。

   ![](assets/s_ncs_user_viral_create_account_form.png)

   >[!NOTE]
   >
   >此配置可进行调整。 为此，您需要修改 **收件人订阅** 存储在 **[!UICONTROL Resources > Online > Web applications]** 节点。
   >
   >有关Web应用程序的详细信息，请参阅 [此部分](../../web/using/about-web-applications.md).

   验证后，系统会向他们发送确认消息：只有在激活确认消息中的链接后，才会永久注册。 此消息基于 **[!UICONTROL Registration confirmation]** 模板，存储在 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 节点。

   裁判被加到 **收件人** 文件夹，并（默认情况下）订阅到 **新闻稿** 信息服务。

## 跟踪社交网络共享 {#tracking-social-network-sharing}

会跟踪共享和访问共享信息的情况。 Adobe Campaign收集的此信息可在以下两个位置访问：

* 在 **[!UICONTROL Tracking]** （或为每个收件人单独设置）：

   ![](assets/s_ncs_user_network_del_tracking_tab.png)

* 在 **[!UICONTROL Sharing to social networks]** 报表：

   ![](assets/s_ncs_user_viral_report.png)
