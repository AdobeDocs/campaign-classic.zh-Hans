---
title: 技术监控
seo-title: 技术监控
description: 技术监控
seo-description: null
page-status-flag: never-activated
uuid: 44ac7cf0-1d44-4656-b137-f3008be32e1d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 008d6a63-68cd-4e87-8adb-9642e2f9bb2a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 38700b79aeb19c75d10d2f5eb60c1efdb12e62e3

---


# 技术监控{#technical-monitoring}

## 技术交付性监控报告 {#technical-deliverability-monitoring}

技术可交付性监视报告会每天更新，并通过导航至 **[!UICONTROL Monitoring]** >并 **[!UICONTROL Overview]** 单击Adobe Campaign选项 **[!UICONTROL Technical monitoring]** 卡中的链接可 **[!UICONTROL Home]** 用。 它包含许多适用于您的平台的可交付性质量指标。

这些指标每天上午9点更新。

>[!NOTE]
>
>此外，您还可以通过电子邮件在指定的地址接收每日报告。 请通过电子邮件或Adobe Campaign Extranet告知我们请求的电子邮件地址。

![](assets/s_tn_del_monitoring.png)

报告中使用了以下指标：

* **[!UICONTROL Reverse DNS]** :Adobe Campaign检查是否为IP地址提供了反向DNS，并且这会正确地指向IP。

* **[!UICONTROL SPF]** （发送方策略框架）:一种身份验证机制，使ISP和邮箱提供商能够检查发送域上的电子邮件发送者是否已获得授权。

   <!--
    >[!NOTE]
    >
    >The SPF may look **[!UICONTROL Acceptable]** (instead of **[!UICONTROL Good]**) since the report is currently unable to detect the presence of a “redirect” or “include” mechanism. This bug has been submitted to Adobe Campaign R&D to be fixed. In the meantime, please feel free to add 15 points to your global score to obtain your real rating (a **[!UICONTROL Good]** one corresponds to 96 points or higher).
    -->

* **[!UICONTROL DomainKeys]** :由Yahoo开发、旨在验证电子邮件发送者身份的服务。

* **[!UICONTROL IP and RBL domain]** （实时黑名单）:区块列表组织标记为发送信誉不佳的IP地址和域的列表。 这些列表由专用组织（如Spamhaus、Spamcop、SURBL/URIBL等）维护。 Adobe Campaign目前针对对交付能力有显着影响的RBL进行检查。 这些RBL反映发送的声誉，在接受接收您的电子邮件之前，ISP可能会引用这些RBL。

* **[!UICONTROL SNDS]** （智能网络数据服务）:Windows [Live Hotmail防垃圾邮件服务](https://sendersupport.olc.protection.outlook.com/snds/FAQ.aspx)。 Hotmail是唯一提供此类信息的ISP。 基准分数是绿色过滤结果，投诉率低于0.1%，垃圾邮件陷阱为零。

<!--
* **[!UICONTROL Reputation Authority]**: This WatchGuard’s score is calculated in real time according to the feedback received from their network worldwide, and also from the different users who use their software.

    Administrators can use such tools to apply a first level filter on their messaging servers.
    If you click on the IP link within the technical report, it will lead you to reputationauthority.org, where you will have the possibility to clean the IP history and get a neutral score again.
    Nevertheless, this action is limited to a number of times per month.
    Please also be aware there is no support provided by WatchGuard‘s Reputation Authority (sending delisting requests is therefore useless). Otherwise, this scoring is based on the following: 
    * Message content (for example: presence of spam words). 
    * IP/Domains reputation (for example: your IPs are listed on an RBL). 
    * IP configuration (for example: IPs associated to different domains). 
    * Volumes sent by IP (for example: presence of peaks or significant variations).
    
    * **[!UICONTROL Sender Score]** : A database of reputed servers ([https://www.senderscore.org/](https://www.senderscore.org/)) issuing a score created by Return Path about your reputation. Think of it like a credit score, but for email senders.-->

<!--## Delivery Reports - Broadcast Statistics {#delivery-reports-broadcast-statistics}

Each delivery will generate a broadcast statistics report when you open a delivery in the “Deliveries List”, which includes some reputation metrics that may impact your deliverability:

![](assets/s_tn_del_monitoring.png)-->
