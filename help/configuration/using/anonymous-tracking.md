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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 7%

---


# 匿名跟踪{#anonymous-tracking}

Adobe Campaign允许您在收集的Web 跟踪信息以匿名方式浏览您的站点时，将其链接到收件人。 当用户浏览您网站的标记页面时，会收集此浏览信息，这样，一旦用户单击由Adobe Campaign发送的电子邮件，就会识别这些用户并自动将这些信息链接到他们。

>[!IMPORTANT]
>
>在网站上设置匿名跟踪可以触发大量跟踪日志的收集，从而影响数据库操作。 谨慎配置。\
>跟踪日志会保存在数据库中，直到清除跟踪数据。 使用部署向导配置清除频率。 如需详细信息，请参阅[此部分](../../installation/using/deploying-an-instance.md#purging-data)。

要对实例启用匿名Web 跟踪，必须配置以下元素：

* 跟 **踪服务器** serverConf.xml文件的元素的trackWebVisitors **参数必须设置为“** trueConf”，在访问该站点的未知用户的Internet浏览器中放置永久Cookie( ************ remonentUuid230Cookie)。
* 必 **须在部署向导** 的跟踪配置屏幕中选择匿名Web 跟踪模式。

   ![](assets/webtracking_anonymous_set.png)

* Web 窗体和调查必须在跟踪服务器上发布和执行。 必须在部署向导中选择匹配选项。

   ![](assets/webtracking_publication_set_for_webapps.png)

