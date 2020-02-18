---
title: 匿名跟踪
seo-title: 匿名跟踪
description: 匿名跟踪
seo-description: null
page-status-flag: never-activated
uuid: 21ba3657-eabf-4228-9fc0-e72712bf8fe7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 2d2c6ae9-4dba-4b82-a25e-eda65a49572d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 匿名跟踪{#anonymous-tracking}

通过Adobe Campaign，当收件人匿名浏览您的网站时，您可以将收集的Web跟踪信息关联到收件人。 当用户浏览您网站的标记页面时，会收集此浏览信息，以便用户在单击由Adobe Campaign发送的电子邮件后，即可识别这些页面，并自动将这些信息链接到这些页面。

>[!IMPORTANT]
>
>在网站上设置匿名跟踪可触发大量跟踪日志的收集，从而影响数据库操作。 谨慎配置。\
>跟踪日志将保存在数据库中，直到清除跟踪数据。 使用部署向导配置清除频率。 如需详细信息，请参阅[此部分](../../installation/using/deploying-an-instance.md#purging-data)。

要对实例启用匿名Web跟踪，必须配置以下元素：

* 必须 **将** serverConf.xml文件元素的 **trackWeb** 参数设置为“ **trueConf.xml** ”，以在未知用户访问网站的Internet浏览器中放置永久Cookie跟踪(******** permonentalUuid20Cookie，即Cookie跟踪)，从而将Internet的WebConf.xml文件元素的WebWebCof参数设置为。
* 必须 **** 在部署向导的跟踪配置屏幕中选择“匿名Web跟踪”模式。

   ![](assets/webtracking_anonymous_set.png)

* 必须在跟踪服务器上发布和执行Web表单和调查。 必须在部署向导中选择匹配选项。

   ![](assets/webtracking_publication_set_for_webapps.png)

