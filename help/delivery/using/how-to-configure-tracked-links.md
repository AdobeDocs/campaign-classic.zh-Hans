---
product: campaign
title: 如何配置跟踪的链接
description: 如何配置跟踪的链接
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: ed88e1d6-c0d5-4a85-9f3e-be670f4bcc10
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 10%

---

# 如何配置跟踪的链接{#how-to-configure-tracked-links}

![](../../assets/common.svg)

对于每次投放，您可以跟踪邮件是否收到，以及邮件内容中插入的链接是否被点击。这样即可在目标投放行动实施后，跟踪收件人的行为。

跟踪适用于消息，但Web跟踪允许您监控收件人浏览网站的方式（访问的页面、购买的页面）。 [此部分](../../configuration/using/about-web-tracking.md)介绍了如何配置 Web 跟踪。

>[!NOTE]
>
>包含个性化的电子邮件内容中的链接需要跟踪特定的语法。 有关如何在电子邮件中添加可个性化且支持跟踪的链接的更多信息，请参阅[此部分](tracking-personalized-links.md)。

我们强烈建议您在应用跟踪公式之前，在&#x200B;**[!UICONTROL Text content]**&#x200B;选项卡的分隔符中引住URL。 您在此选项卡中输入的URL分隔符将由Adobe Campaign用于标识字符串内的URL。 您可以使用以下分隔符对：
* 括号()
* 括号[ ]
* 大括号{ }

在此示例中，URL https://www.adobe.com后面跟有一个分号。 收件人电子邮件客户端可以将分号解释为URL的一部分。 因此，链接可能会断开。 要避免出现此问题，您可以使用以下方式之一将URL括在分隔符中：
* (https://www.adobe.com);
* [https://www.adobe.com];
* {https://www.adobe.com};

默认启用消息跟踪。 要个性化URL的跟踪方式，请执行以下步骤：

1. 在投放向导的下半部分中，选择消息内容下的&#x200B;**[!UICONTROL Display URLs]**&#x200B;选项。

   ![](assets/s_ncs_user_email_del_display_urls.png)

   当您从跟踪的URL列表中选择URL时，该URL会在投放内容中突出显示 — 但镜像页面中的链接和默认提供的退订链接除外。

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. 对于消息的每个URL，选择是否激活跟踪。

   >[!IMPORTANT]
   >
   >当链接的URL用作标签时，建议停用跟踪以避免因网络钓鱼而被拒绝的风险。
   >
   >例如，如果将www.adobe.com URL插入消息中并激活该消息的跟踪，则超文本链接的内容将被修改为https://nlt.adobe.net/r/?id=xxxxxx。 这意味着收件人消息客户端可能会将其视为欺诈。

1. 如果需要，请更改跟踪标签，双击该标签并输入新标签。

   >[!NOTE]
   >
   >可以修改跟踪URL的标签和标签，以简化跟踪投放时的信息读取。 在计算点击次数时，将同时添加两个或两个同名的URL。

1. 如果需要，请更改跟踪模式，在&#x200B;**[!UICONTROL Tracking]**&#x200B;列中选择与目标链接匹配的新模式，如下所示：

   ![](assets/s_ncs_user_select_tracking_mode.png)

   对于每个URL，您可以将跟踪模式设置为以下值之一：

   * **[!UICONTROL Enabled]** :在此URL上激活跟踪。
   * **[!UICONTROL Not tracked]** :停用对此URL的跟踪。
   * **[!UICONTROL Always enabled]** :始终激活此URL的跟踪。此信息已保存，以便下次，如果URL在将来的消息内容中再次显示，则其跟踪将自动激活。
   * **[!UICONTROL Never tracked]** :从不激活此URL的跟踪。此信息已保存，以便下次，如果URL在将来的消息中再次显示，则其跟踪将自动停用。
   * **[!UICONTROL Opt-out]** :将此URL视为选择退订或退订URL。
   * **[!UICONTROL Mirror page]** :将此URL视为镜像页面URL。

1. 此外，您还可以在&#x200B;**[!UICONTROL Category]**&#x200B;列的下拉列表中为每个跟踪的URL选择一个类别。 这些类别可以显示报表，例如在&#x200B;**[!UICONTROL URLs and click streams]**&#x200B;中（请参阅[此部分](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)）。 类别在特定枚举中定义：**[!UICONTROL urlCategory]**（请参阅[管理枚举](../../platform/using/managing-enumerations.md)）。
