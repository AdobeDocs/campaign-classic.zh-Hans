---
product: campaign
title: 匿名跟踪
description: 了解如何设置匿名跟踪
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: f251eb21-0f3c-4b46-927a-57a3291e705f
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 5%

---

# 匿名跟踪{#anonymous-tracking}

通过Adobe Campaign，您可以在收件人匿名浏览您的网站时将收集的Web跟踪信息链接到收件人。 当用户浏览网站的标记页面时，将收集此浏览信息，以便他们单击Adobe Campaign发送的电子邮件后，即会识别这些页面，并且信息会自动链接到这些页面。

>[!IMPORTANT]
>
>在网站上设置匿名跟踪可能会触发收集大量跟踪日志，从而影响数据库操作。 请谨慎配置。\
>跟踪日志将保存在数据库中，直到清除跟踪数据为止。 使用部署向导配置清除频率。 如需详细信息，请参阅[此部分](../../installation/using/deploying-an-instance.md#purging-data)。

要在实例上启用匿名Web跟踪，必须配置以下元素：

* 此 **trackWebVisitors** 的参数 **重定向** 元素 **serverConf.xml** 必须将跟踪服务器的文件设置为&#39;**true**`，以放置永久Cookie(**uuid230**)，这些浏览器为访问网站的未知Internet用户。
* 此 **匿名Web跟踪** 必须在部署向导的跟踪配置屏幕中选择模式。

   ![](assets/webtracking_anonymous_set.png)

* 必须在跟踪服务器上发布和执行Web窗体。 必须在部署向导中选择匹配选项。

   ![](assets/webtracking_publication_set_for_webapps.png)
