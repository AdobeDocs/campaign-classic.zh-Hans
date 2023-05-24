---
product: campaign
title: 如何配置跟踪的链接
description: 如何配置跟踪的链接
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring
exl-id: ed88e1d6-c0d5-4a85-9f3e-be670f4bcc10
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 10%

---

# 如何配置跟踪的链接{#how-to-configure-tracked-links}



对于每次投放，您可以跟踪邮件是否收到，以及邮件内容中插入的链接是否被点击。这样即可在目标投放行动实施后，跟踪收件人的行为。

跟踪适用于消息，但Web跟踪允许您监控收件人浏览网站的方式（访问的页面、购买情况）。 [此部分](../../configuration/using/about-web-tracking.md)介绍了如何配置 Web 跟踪。

>[!NOTE]
>
>包含个性化的电子邮件内容中的链接，需要跟踪特定的语法。 有关如何添加可个性化并支持跟踪的电子邮件链接的更多信息，请参阅 [本节](tracking-personalized-links.md).

我们强烈建议您将URL **[!UICONTROL Text content]** 选项卡。 Adobe Campaign会使用您在此选项卡中输入的URL分隔符来标识字符串中的URL。 您可以使用以下分隔符对：
* 括号( )
* 括号 [ ]
* 大括号{ }

在此示例中，URL https://www.adobe.com后跟一个分号。 分号可由收件人电子邮件客户端解释为URL的一部分。 因此，链接可能会断开。 要避免出现此问题，您可以通过以下方式之一用分隔符括住URL：
* (https://www.adobe.com)；
* [https://www.adobe.com]；
* {https://www.adobe.com}；

默认启用消息跟踪。 要个性化URL的跟踪方式，请执行以下步骤：

1. 选择 **[!UICONTROL Display URLs]** 选项（位于投放向导的下部，消息内容下）。

   ![](assets/s_ncs_user_email_del_display_urls.png)

   从跟踪的URL列表中选择某个URL后，投放内容中将高亮显示该链接，但镜像页面中的链接和默认提供的退订链接除外。

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. 对于消息的每个URL，选择是否激活跟踪。

   >[!IMPORTANT]
   >
   >当链接的URL用作标签时，建议取消激活跟踪，以避免因网络钓鱼而被拒绝的风险。
   >
   >例如，如果将www.adobe.com URL插入到消息中并在其上激活跟踪，则超文本链接的内容将被修改为https://nlt.adobe.net/r/?id=xxxxxx。 这意味着收件人消息客户端可以将其视为欺诈。

1. 如果需要，请更改跟踪标签，双击该标签并输入新标签。

   >[!NOTE]
   >
   >可修改跟踪的URL和标签的标签，以简化跟踪投放时信息的阅读。 计算点击计数时，会将两个具有相同名称的URL或两个标签相加。

1. 如果需要，请更改跟踪模式，然后在 **[!UICONTROL Tracking]** 与定向链接匹配的列，如下所示：

   ![](assets/s_ncs_user_select_tracking_mode.png)

   对于每个单个URL，您可以将跟踪模式设置为以下值之一：

   * **[!UICONTROL Enabled]** ：在此URL上激活跟踪。
   * **[!UICONTROL Not tracked]** ：停用此URL上的跟踪。
   * **[!UICONTROL Always enabled]** ：始终激活此URL的跟踪。 保存此信息，以便下次如果URL再次出现在将来的消息内容中，则会自动激活其跟踪。
   * **[!UICONTROL Never tracked]** ：从不激活此URL的跟踪。 保存此信息，以便下次如果URL再次出现在将来的消息中，则会自动停用其跟踪。
   * **[!UICONTROL Opt-out]** ：将此URL视为选择退出或退订URL。
   * **[!UICONTROL Mirror page]** ：将此URL视为镜像页面URL。

1. 此外，您还可以从的下拉列表中为每个跟踪的URL选择一个类别 **[!UICONTROL Category]** 列。 这些类别可以显示报表，例如 **[!UICONTROL URLs and click streams]** (请参阅 [本节](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams))。 类别在特定枚举中定义： **[!UICONTROL urlCategory]** (请参阅 [管理明细列表](../../platform/using/managing-enumerations.md))。
