---
product: campaign
title: 匿名跟踪
description: 匿名跟踪
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: ee3d643e4ba607b3d7ca816eabf862b867d1f3f4
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 6%

---

# 匿名跟踪{#anonymous-tracking}

Adobe Campaign允许您在收集的Web跟踪信息以匿名方式浏览您网站时，将其链接到收件人。 当用户浏览您网站的标记页面时，会收集此浏览信息，以便用户在单击由Adobe Campaign发送的电子邮件后，即会识别这些用户，并且该信息会自动链接到这些用户。

>[!IMPORTANT]
>
>在网站上设置匿名跟踪可能会触发大量跟踪日志的收集，从而影响数据库操作。 小心配置。\
>跟踪日志会保存在数据库中，直到清除跟踪数据为止。 使用部署向导配置清除频率。 如需详细信息，请参阅[此部分](../../installation/using/deploying-an-instance.md#purging-data)。

要在实例上启用匿名Web跟踪，必须配置以下元素：

* 跟踪服务器的&#x200B;**serverConf.xml**&#x200B;文件的&#x200B;**trackWebVisitors**&#x200B;重定向&#x200B;**元素的** trackWebVisitors参数必须设置为“**true**”，以便在访问该站点的未知Internet用户的浏览器中放置永久Cookie(**uid230**)。
* 必须在部署向导的跟踪配置屏幕中选择&#x200B;**匿名Web跟踪**&#x200B;模式。

   ![](assets/webtracking_anonymous_set.png)

* 必须在跟踪服务器上发布和执行Web窗体。 必须在部署向导中选择匹配选项。

   ![](assets/webtracking_publication_set_for_webapps.png)
