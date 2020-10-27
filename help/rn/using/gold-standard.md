---
title: Gold Standard 发行
description: Campaign Classic金标发行说明
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: 877ca2275c9338377da9e435e070c9911314fe51
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 15%

---


# Gold Standard 发行{#gold-standard}

Gold Standard是Campaign Classic长期支持版本。 作为金标用户，您无需采取任何操作，即可通过最新稳定版本自动从金标升级中受益。 内部部署和混合型客户还可以从Gold Standard版本中受益。

如果您从旧版本进行迁移，我们建议您先升级到此版本。

本页列表Gold Standard版本。

有关活动金本位项目的详细信息，请 [参阅本文](https://helpx.adobe.com/cn/campaign/kb/gold-standard.html)。

## ![](assets/do-not-localize/green_2.png) 金标10版{#gs-10}

_2020年7月7日_

内部版本9032@efd8a94包含以下修复：

修复了在禁用签名功能时跟踪无法工作的问题。 (NEO-26411)

>[!CAUTION]
>
>我们建议您使用此版本中提供的客户端控制台进行升级。 Refer [to this page](../../installation/using/installing-the-client-console.md)

## ![](assets/do-not-localize/red_2.png) Gold Standard 9版{#gs-9}

_2020年6月22日_

内部版本9032@800be2e包括以下修复：

* iOS HTTP2连接器已得到改进（第三方更新和错误管理）。 (NEO-25904、NEO-25903、NEO-25799)

以下修复与跟踪链接安全机制相关(请参阅安全和隐私核对 [清单了解更多](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)):

* 修复了导致跟踪“通知单击”无法正常工作的问题（iOS和Android推送通知）。 (NEO-25965)
* 修复了在使用某些旧版Outlook时无法打开／单击跟踪URL的问题。  (NEO-25688)
* 修复了在个性化参数（带磅签名的锚点标记）中使用片段跟踪URL时无法正常工作的问题。 (NEO-25774)
* 修复了反网络钓鱼服务的问题。 (NEO-25283)
* 修复了使用特定自定义跟踪公式时的跟踪问题。 (NEO-25277)

## ![](assets/do-not-localize/red_2.png) Gold Standard 8版{#gs-8}

_2020年4月29日_

内部版本9032@3a9dc9c包括以下修复：

* 改进了跟踪电子邮件链接的安全性。 默认情况下，所有客户都启用此功能。 另外还提供了增强的安全功能，可通过联系客户服务中心来启用此功能。有关此功能及非托管客户启用此功能的步骤的更多详细信息，请参阅[安全和隐私检查列表](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)。

>[!CAUTION]
>
>如果您在使用跟踪链接的推送通知或使用锚点标记的投放时遇到问题，建议您禁用用于跟踪链接的新签名机制。 该过程在本 [页中详述](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)

* 修复了一个问题，该问题可能会阻止图像显示在行投放上。 (NEO-23207)
* 修复了&#x200B;**文件传输**&#x200B;活动的问题，该问题导致基于 SFTP 密钥的身份验证无法在 Debian 9 上工作。(NEO-23183)
* 修复了在以高频率发送时可能影响推送通知的问题。 (NEO-20516)
* 修复了优惠响应管理中可能导致Web服务器崩溃的问题。 (NEO-19482)
* 修复了LibreOffice管理中阻止导出报告的错误。 (NEO-20982)
* 修复了使用工作流活动升级大量调查时导致错误的问题。
* 改进了LibreOffice管理，以避免在电子邮件预览中使用。odt文件失败。
* 改进了Apache连接的管理以避免Web服务上的延迟。
* 改进了版本标签（7位数）在“关于”菜单 **中的显** 示。
* 修复了列表管理中的回归，阻止优惠发布。
* 修复了导致清理工作流崩溃的回归。
* 修复了清理工作流日志中的次要回归。

## ![](assets/do-not-localize/orange_2.png) 金标6版{#gs-6}

_2020年3月9日_

内部版本9032@19f73c5包含以下修复：

* 修复了外部帐户使用 FTP over SSL 时的问题。(NEO-20498)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 5版{#gs-5}

_2019年12月17日_

内部版本9032@d6b8062包含以下修复：

* 修复了以下通信渠道的跟踪问题：移动(SMS、MMS)、推送(iOS、Android)和社交网络(Facebook、Twitter)。 (NEO-19595)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 4版{#gs-4}

_2019年12月11日_

内部版本9032@bc4a935包含以下修复：

* 修复了使用MSSQL数据库发送消息时的性能问题。 (NEO-17558)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 3版本{#gs-3}

_2019年11月20日_

内部版本9032@3468c7b包括以下修复：

* 修复了通过IMS身份验证的登录问题。 (NEO-17312)
* 修复了在多个投放上显示累积报告时的问题。 (NEO-18165)
* 修复了可能阻止或导致Web服务器崩溃的问题。

## ![](assets/do-not-localize/red_2.png) Gold Standard 2版{#gs-2}

_2019年9月19日_

内部版本9032@cee805c包括以下修复：

* 修复了在使用Salesforce的CRM连接器时的问题。 (NEO-17712)
* 修复了在发送事务性消息时可能导致性能问题的索引问题。

## ![](assets/do-not-localize/red_2.png) 版本 19.1.4 - 版本 9032{#release-19-1-4-build-9032}

_2019年8月13日_

初始19.1.4版本包括以下修复：

* 修复了调度程序活动在向导配置过程中生成不需要的错误消息的问题。 正在还原NEO-11662的更新。 (NEO-17097)
* 修复了由NEO-12727引起的回归，该回归可能导致在执行两次测试工作流时停止活动。 (NEO-16835)
* 修复了在API调用中使用无效或过期的会话令牌时，导致返回错误的HTTP代码（HTTP 200 OK而非HTTP 403已禁止）的问题。 (NEO-16826)
* 修复了DKIM密钥的问题，该问题不再嵌入到电子邮件中，从而导致交付性问题。 (NEO-16804)
* 修复了工作流计划的各种问题。 工作流计划每天执行一次，而不考虑调度程序配置。 (NEO-16619, NEO-16426)
