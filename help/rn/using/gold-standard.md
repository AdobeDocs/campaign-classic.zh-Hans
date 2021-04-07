---
solution: Campaign Classic
product: campaign
title: '[!DNL Gold Standard] 发行说明'
description: Campaign Classic [!DNL Gold Standard]发行说明
feature: 概述
role: Business Practitioner
level: Beginner
exl-id: 9e3a11b1-3070-4d90-91d5-7c559bdd500e
translation-type: tm+mt
source-git-commit: 6854d06f8dc445b56ddfde7777f02916a60f2b63
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 96%

---

# [!DNL Gold Standard] 发行说明{#gold-standard}

本页列表[!DNL Gold Standard]版本。 了解有关活动[!DNL Gold Standard] [的更多信息，请参阅此页](gs-overview.md)。

## ![](assets/do-not-localize/green_2.png) [!DNL Gold Standard] 11版{#gs-11}

_2021 年 3 月 2 日_

内部版本 9032@10c2709 包含以下修复：

* 修复了导致无法使用某些控制台组件（如投放中的日期选择器和图像管理）的回退问题。(NEO-31453, NEO-31454)

**必须执行仅控制台升级。无需升级服务器。**

>[!NOTE]
>
> 连接到 [Adobe Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html) 以下载新版本。 [在此页面中](../../installation/using/client-console-availability-for-windows.md)了解如何向所有最终用户建议更新控制台。


_2020 年 12 月 22 日_

>[!CAUTION]
>
> * 此版本附带新的连接协议：如果您是通过 Adobe Identity Service (IMS) 连接到 Campaign，则 Campaign 服务器和客户端控制台都必须升级，这样才能在&#x200B;**2021 年 6 月 30 日**&#x200B;之后连接到 Campaign。
> * 此版本附带[安全修复](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)：必须升级以增强环境安全性。
> * 如果您是通过 oAuth 身份验证使用 Experience Cloud Triggers 集成，则需要按照[此页面](../../integrations/using/configuring-adobe-io.md)中的说明移至 Adobe I/O。Campaign 的旧式 oAuth 身份验证模式将于 **2021 年 11 月 30 日**&#x200B;停用。

>
>
在[[!DNL Gold Standard] 11升级常见问题解答](https://helpx.adobe.com/cn/campaign/kb/gold-standard-upgrade.html)中了解更多信息。

内部版本 9032@d3b452f 包括以下改进和修复：

* 连接协议已经更新，以遵循新的 IMS 认证机制。

* 最初基于 oAUTH 身份验证设置来访问管道的 Triggers 集成身份验证现已更改并移至 Adobe I/O。[了解详情](../../integrations/using/configuring-adobe-io.md)

* [终止支持 iOS APN 旧版二进制协议](https://developer.apple.com/news/?id=c88acm2b)之后，在升级后期间，所有使用此协议的实例都更新为 HTTP/2 协议。

* 修复了一个安全问题，以加强针对服务器端请求伪造 (SSRF) 问题的防范。(NEO-27777)

* 修复了在运行&#x200B;**扩充**&#x200B;活动时可能导致工作流失败的问题。(NEO-17338)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 10版{#gs-10}

_2020 年 7 月 7 日_

内部版本 9032@efd8a94 包含以下修复：

修复了在禁用签名功能时跟踪无法正常工作的问题。(NEO-26411)

>[!CAUTION]
>
>我们建议您使用此版本中提供的客户端控制台进行升级。请参见[此页面](../../installation/using/installing-the-client-console.md)。

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 9版{#gs-9}

_2020 年 6 月 22 日_

内部版本 9032@800be2e 包含以下修复：

* iOS HTTP2 连接器已得到改进（第三方更新和错误管理）。(NEO-25904、NEO-25903、NEO-25799)

以下修复与跟踪链接安全机制相关（在[安全和隐私核对清单](https://helpx.adobe.com/cn/campaign/kb/acc-security.html#signature-mechanism)中了解更多信息）：

* 修复了跟踪“通知点击量”无法正常工作的问题（iOS 和 Android 推送通知）。(NEO-25965)
* 修复了在使用某些旧版 Outlook 时可能导致无法打开/单击跟踪 URL 的问题。  (NEO-25688)
* 修复了在使用个性化参数（带井号的锚点标记）中的片段跟踪 URL 时无法正常工作的问题。(NEO-25774)
* 修复了反网络钓鱼服务的问题。(NEO-25283)
* 修复了使用特定自定义跟踪公式时的跟踪问题。(NEO-25277)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 8版{#gs-8}

_2020 年 4 月 29 日_

内部版本 9032@3a9dc9c 包含以下修复：

* 改进了电子邮件中跟踪链接的安全性。默认情况下，所有客户都启用此功能。另外还提供了增强的安全功能，可通过联系客户服务中心来启用此功能。有关此功能及非托管客户启用此功能的步骤的更多详细信息，请参阅[安全和隐私检查列表](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)。

>[!CAUTION]
>
>如果您在使用跟踪链接时遇到推送通知问题，或在使用锚点标记时遇到投放问题，建议您禁用跟踪链接的新签名机制。[此页面中](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)对该过程进行了详述

* 修复了可能会导致图像无法在 Line 投放中显示的问题。(NEO-23207)
* 修复了&#x200B;**文件传输**&#x200B;活动的问题，该问题导致基于 SFTP 密钥的身份验证无法在 Debian 9 上工作。(NEO-23183)
* 修复了在以高频率发送时可能影响推送通知的问题。(NEO-20516)
* 修复了优惠响应管理中可能导致 Web 服务器崩溃的问题。(NEO-19482)
* 修复了 LibreOffice 管理中阻止导出报告的错误。(NEO-20982)
* 修复了使用调查活动升级大量工作流时导致错误的问题。
* 改进了 LibreOffice 管理，以避免使用 .odt 文件进行电子邮件预览失败。
* 改进了 Apache 连接的管理，以避免 Web 服务延迟。
* 改进了&#x200B;**关于**&#x200B;菜单中版本标记（7 位数）的显示。
* 修复了列表管理中阻止发布优惠的回归。
* 修复了导致清理工作流崩溃的回归。
* 修复了清理工作流日志中的次要回归。

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 6版{#gs-6}

_2020 年 3 月 9 日_

内部版本 9032@19f73c5 包含以下修复：

* 修复了外部帐户使用 FTP over SSL 时的问题。(NEO-20498)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 5版{#gs-5}

_2019 年 12 月 17 日_

内部版本 9032@d6b8062 包含以下修复：

* 修复了以下通信渠道上的跟踪问题：移动（SMS 或 MMS）、推送（iOS 或 Android）和社交网络（Facebook 或 Twitter）。(NEO-19595)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 4版{#gs-4}

_2019 年 12 月 11 日_

内部版本 9032@bc4a935 包含以下修复：

* 修复了使用 MSSQL 数据库发送消息时的性能问题。(NEO-17558)

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 3版{#gs-3}

_2019 年 11 月 20 日_

内部版本 9032@3468c7b 包含以下修复：

* 修复了通过 IMS 身份验证进行登录的问题。(NEO-17312)
* 修复了在多个投放中显示累积报告时的问题。(NEO-18165)
* 修复了可能出现拦截或导致 Web 服务器崩溃的问题。

## ![](assets/do-not-localize/red_2.png) [!DNL Gold Standard] 2版{#gs-2}

_2019 年 9 月 19 日_

内部版本 9032@cee805c 包含以下修复：

* 修复了使用 CRM Connector for Salesforce 时的问题。(NEO-17712)
* 修复了在发送事务性消息时可能导致性能问题的索引问题。

## ![](assets/do-not-localize/red_2.png) 版本 19.1.4 - 版本 9032{#release-19-1-4-build-9032}

_2019 年 8 月 13 日_

初始 19.1.4 内部版本包含以下修复：

* 修复了调度程序活动在向导配置期间生成不需要的错误消息的问题。NEO-11662 中的“还原更新”。(NEO-17097)
* 修复了 NEO-12727 引起的回归，该回归可能导致在执行两次测试活动时停止工作流。(NEO-16835)
* 修复了在 API 调用中使用无效或过期的会话令牌时导致返回错误的 HTTP 代码（HTTP 200 OK 而非 HTTP 403 Forbidden）的问题。(NEO-16826)
* 修复了 DKIM 密钥的问题，该密钥不再嵌入到电子邮件中，从而导致投放能力问题。(NEO-16804)
* 修复了工作流调度的各种问题。工作流已调度为每天执行一次，而不考虑调度程序配置。(NEO-16619, NEO-16426)
