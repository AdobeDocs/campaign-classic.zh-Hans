---
title: 如何配置跟踪的链接
seo-title: 如何配置跟踪的链接
description: 如何配置跟踪的链接
seo-description: null
page-status-flag: never-activated
uuid: 0fb41a43-8a84-4a61-bf93-97e1d448a5ec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 9cae3861-88eb-447a-aa23-9d1de0710eec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 如何配置跟踪的链接{#how-to-configure-tracked-links}

对于每次投放，您可以跟踪邮件是否收到，以及邮件内容中插入的链接是否被点击。这样即可在目标投放行动实施后，跟踪收件人的行为。

>[!NOTE]
>
>跟踪适用于消息，但Web跟踪允许您监视收件人浏览网站的方式（访问的页面、购买）。
>
>本节介绍了Web跟踪的 [配置](../../configuration/using/about-web-tracking.md)。

默认情况下，消息跟踪处于启用状态。 要个性化跟踪URL的方式，请执行以下步骤：

1. 在分 **[!UICONTROL Display URLs]** 发向导的下半部分，在消息内容下选择选项。

   ![](assets/s_ncs_user_email_del_display_urls.png)

   从跟踪的URL列表中选择URL后，该URL将在交付内容中高亮显示——但镜像页面中的链接和默认提供的取消订阅链接除外。

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. 对于消息的每个URL，选择是否激活跟踪。

   >[!CAUTION]
   >
   >当链接的URL用作标签时，建议取消激活跟踪以避免网络钓鱼导致拒绝的风险。
   >
   >例如，如果将www.adobe.com URL插入消息中并在消息上激活了跟踪，则超文本链接的内容将修改为https://nlt.adobe.net/r/?id=xxxxxx。 这意味着收件人消息客户端可能认为它具有欺骗性。

1. 如果需要，请更改跟踪标签，双击该标签并输入新标签。

   >[!NOTE]
   >
   >可以修改跟踪的URL的标签和标签，以简化跟踪分发时的信息读取。 在计算点击计数时，将添加两个或两个同名的URL。

1. 如果需要，请更改跟踪模式，在列中选择与目标链接 **[!UICONTROL Tracking]** 匹配的新模式，如下所示：

   ![](assets/s_ncs_user_select_tracking_mode.png)

   对于每个URL，可以将跟踪模式设置为以下值之一：

   * **[!UICONTROL Enabled]** :激活对此URL的跟踪。
   * **[!UICONTROL Not tracked]** :禁用此URL上的跟踪。
   * **[!UICONTROL Always enabled]** :始终激活此URL的跟踪。 此信息会保存，这样，下次，如果URL再次出现在将来的消息内容中，则其跟踪会自动激活。
   * **[!UICONTROL Never tracked]** :从不激活此URL的跟踪。 此信息会保存，这样，下次，如果URL再次显示在将来的消息中，则其跟踪会自动停用。
   * **[!UICONTROL Opt-out]** :将此URL视为选择退出或取消订阅URL。
   * **[!UICONTROL Mirror page]** :将此URL视为镜像页面URL。

1. 此外，您还可以在列的下拉列表中选择每个跟踪的URL的类 **[!UICONTROL Category]** 别。 这些类别可以显示报告，如中所示 **[!UICONTROL URLs and click streams]** (请参 [阅此部分](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams))。 类别在特定枚举中定义：(请 **[!UICONTROL urlCategory]** 参阅 [管理枚举](../../platform/using/managing-enumerations.md))。
