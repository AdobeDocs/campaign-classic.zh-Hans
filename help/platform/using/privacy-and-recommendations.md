---
title: 隐私和建议
seo-title: 隐私和建议
description: 隐私和建议
seo-description: null
page-status-flag: never-activated
uuid: a044bbea-521d-4c1e-8aab-7d51a87fc94b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
discoiquuid: 14369acf-9149-4649-947a-c16289e35eb6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ed5390b4f620c3cddaf9b856f3354dc5f06f4d98

---


# 隐私和建议{#privacy-and-recommendations}

## 有关隐私及许可 {#about-privacy-and-consent}

Adobe Campaign 是一款用于收集和处理超大量数据（包括个人信息）的强大工具。我们鼓励Adobe Campaign的所有用户在法规（DPA、CAN-SPAM、欧洲隐私和电子通信指令、欧洲GDPR等）范围内工作，对个人信息进行负责任和合乎道德的使用，并避免发送主动提供的电子邮件、推送通知和SMS消息（“垃圾邮件”）。 为了实现客户终生价值并提高客户忠诚度，我们坚信许可营销原则，也因此严格禁止使用 Adobe Campaign 发送未经请求的消息。

如需详细信息，请参阅 [Adobe Experience Cloud 隐私政策](https://www.adobe.com/privacy/marketing-cloud.html)。

Adobe Campaign 提供了各种工具、功能以及最佳实践，帮助您在使用我们的服务时遵循 GDPR。请参阅[本文档](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/ACC_GDPR.html)。

请查看[安全和隐私检查列表](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)，了解有关安全和隐私方面需要检查的核心元素。

## Cookie 和跟踪功能 {#cookies-and-tracking-capabilities}

借助跟踪功能，您能够使用 Adobe Campaign 跟踪投放内容的接收者在网站上的浏览痕迹。Adobe Campaign 使用会话 Cookie 和永久性 Cookie 实现上述功能。

欧盟的“隐私及电子通信”指令 2009/136/CE 和欧盟一般数据保护条例 (GDPR) 规定，公司在安装任何 Cookie 之前都需要获得网站用户的同意。您必须通过授权请求（有时出现在页面上方）告知用户，您网站已配备了 Web 跟踪工具并要求用户选中复选框来授权安装 Cookie，或者在用户登陆的首页顶端添加横幅等。不要使用弹出式窗口，因为浏览器通常会拦截此类窗口。

在 Web 应用程序以及带有选择退出横幅的登陆页面上都可以配置用户跟踪管理功能。请参见[此页面](../../web/using/web-application-tracking-opt-out.md)。

Adobe Campaign 使用两种类型的 Cookie：

1. 会话 Cookie (nlid)：它包含发送到联系人的电子邮件的标识符 (broadlogId)，以及消息模板的标识符 (deliveryId)。联系人单击由 Adobe Campaign 发送的电子邮件中包含的 URL 后即可添加标识符，让您能够跟踪他们在网络上的行为。关闭浏览器时，将自动擦除会话 Cookie。联系人可以将浏览器配置为拒绝 Cookie。
1. 永久性 Cookie (uuid230)：它让您在用户访问网站时，能够识别出与 Adobe Campaign 互动的用户。Adobe Campaign 可使用该 Cookie 计算在市场营销活动中的点击数并估算用户转换率。联系人在电子邮件中点击、在 Adobe Campaign 中填写窗体内容或在入站互动引擎呼叫期间，都将放置此 Cookie。用户可以将浏览器配置为删除或拒绝 Cookie。

## 数据库完整性 {#database-integrity}

Adobe Campaign 拥有丰富的功能。因此，它使用了复杂的数据库结构。数据库中包含许多表、字段、链接以及索引。某些中间表未显示在界面中。该软件会自动创建、删除或修改某些链接、字段和索引。只有 Adobe Campaign 界面（图形界面、导入程序、服务器模块、Web 模块、投放服务器、添加字段、数据库扩展等）可以修改数据库的内容，同时保持数据库的完整性。

**切勿使用此软件以外的任何工具修改数据库內容或结构**。此类修改极有可能损坏数据库，导致：意外修改或链接丢失、创建虚影记录或链接、严重错误消息等，或者导致 Adobe Campaign 提供的担保与技术支持合同无效或废止。

在 Adobe Campaign 系统中，所有数据都存储在数据库中。能否正确使用整个 Adobe Campaign 系统取决于以下数据的可用性：用于订阅、管理和退订的网络模块，以及管理屏幕、投放队列、投放优化机制等。

## Apache Tomcat {#apache-tomcat}

Adobe Campaign 包含由 Apache Software Foundation ([https://www.apache.org/](https://www.apache.org/)) 开发的 Apache Tomcat。
