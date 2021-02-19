---
solution: Campaign Classic
product: campaign
title: 匿名跟踪
description: 匿名跟踪
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 6%

---


# 匿名跟踪{#anonymous-tracking}

Adobe Campaign允许您在收集的Web 跟踪信息以匿名方式浏览您的站点时，将其链接到收件人。 当用户浏览您网站的标记页面时，会收集此浏览信息，以便用户在单击由Adobe Campaign发送的电子邮件后，即会识别这些信息，并自动将该信息链接到它们。

>[!IMPORTANT]
>
>在网站上设置匿名跟踪可以触发大量跟踪日志的收集，从而影响数据库操作。 谨慎配置。\
>跟踪日志将保存在数据库中，直到清除跟踪数据。 使用部署向导配置清除频率。 如需详细信息，请参阅[此部分](../../installation/using/deploying-an-instance.md#purging-data)。

要在实例上启用匿名Web 跟踪，必须配置以下元素：

* 必须将跟踪服务器的&#x200B;**serverConf.xml**&#x200B;文件的&#x200B;**重定向**&#x200B;元素的&#x200B;**trackWebVisitors**&#x200B;参数设置为“**true**”，以在中放置永久cookie(**uuid230**)访问网站的未知Internet用户的浏览器。
* 必须在部署向导的跟踪配置屏幕中选择&#x200B;**匿名Web 跟踪**&#x200B;模式。

   ![](assets/webtracking_anonymous_set.png)

* Web 窗体和调查必须在跟踪服务器上发布和执行。 必须在部署向导中选择匹配选项。

   ![](assets/webtracking_publication_set_for_webapps.png)

