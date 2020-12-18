---
solution: Campaign Classic
product: campaign
title: 如何配置跟踪的链接
description: 如何配置跟踪的链接
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 11%

---


# 如何配置跟踪的链接{#how-to-configure-tracked-links}

对于每次投放，您可以跟踪邮件是否收到，以及邮件内容中插入的链接是否被点击。这样即可在目标投放行动实施后，跟踪收件人的行为。

>[!NOTE]
>
>跟踪适用于消息，但Web跟踪允许您监视收件人浏览网站（访问的页面、购买）的方式。
>
>Web跟踪的配置显示在[本节](../../configuration/using/about-web-tracking.md)中。

默认情况下，消息跟踪处于启用状态。 要个性化跟踪URL的方式，请执行以下步骤：

1. 选择投放向导下半部分消息内容下的&#x200B;**[!UICONTROL Display URLs]**&#x200B;选项。

   ![](assets/s_ncs_user_email_del_display_urls.png)

   当您从跟踪的URL列表中选择URL时，该URL将在投放内容中高亮显示——默认情况下提供的镜像页面和退订链接除外。

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. 对于邮件的每个URL，选择是否激活跟踪。

   >[!IMPORTANT]
   >
   >当链接的URL用作标签时，建议取消激活跟踪以避免由于网络钓鱼而被拒绝的风险。
   >
   >例如，如果将www.adobe.com URL插入消息并激活了该消息的跟踪，则超文本链接的内容将修改为https://nlt.adobe.net/r/?id=xxxxxx。 这意味着收件人消息客户端可能认为它具有欺骗性。

1. 如果需要，请更改跟踪标签，多次单击标签并输入新标签。

   >[!NOTE]
   >
   >跟踪的URL的标签和标签可以修改，以简化跟踪投放时的信息读取。 计算点击计数时，将同时添加两个或两个同名的URL。

1. 如果需要，请更改跟踪模式，在&#x200B;**[!UICONTROL Tracking]**&#x200B;列中选择与目标链接匹配的新模式，如下所示：

   ![](assets/s_ncs_user_select_tracking_mode.png)

   对于每个URL，可以将跟踪模式设置为以下值之一：

   * **[!UICONTROL Enabled]** :在此URL上激活跟踪。
   * **[!UICONTROL Not tracked]** :禁用此URL上的跟踪。
   * **[!UICONTROL Always enabled]** :始终激活此URL的跟踪。此信息会保存，这样，如果下次URL再次出现在将来的消息内容中，其跟踪将自动激活。
   * **[!UICONTROL Never tracked]** :从不激活此URL的跟踪。此信息将保存，这样，如果下次URL再次出现在将来的消息中，其跟踪将自动取消激活。
   * **[!UICONTROL Opt-out]** :将此URL视为退出或退订URL。
   * **[!UICONTROL Mirror page]** :将此URL视为镜像页面URL。

1. 此外，您还可以在&#x200B;**[!UICONTROL Category]**&#x200B;列的下拉类别中为每个跟踪的URL选择一个列表。 这些类别可以显示报告，如&#x200B;**[!UICONTROL URLs and click streams]**（请参阅[此部分](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)）。 类别在特定明细列表中定义：**[!UICONTROL urlCategory]**(请参阅[管理明细列表](../../platform/using/managing-enumerations.md))。
