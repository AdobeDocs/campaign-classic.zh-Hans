---
title: 连接失败
seo-title: 连接失败
description: 连接失败
seo-description: null
page-status-flag: never-activated
uuid: 5e4cf47d-9699-4b4c-9c45-064fdc17110a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 493067fb-68f1-48b9-afaa-3127a847db83
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 90813bc2913d56136067b9f64c0e934df3f17473

---


# 连接失败{#failure-to-connect}

这种情况的原因可能是多重的，并取决于不同的上下文。

检查安全区域的常规配置。

>[!NOTE]
>
>有关配置安全区域的详细信息，请参 [阅此部分](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

检查以下信息：

1. **网络检查**

   * 您是否可以从计算机访问Internet?

      检查是否可以连接到Internet上的网站（例如）。 如果无法连接，则问题出在您的计算机上。 联系您的系统管理员。

   * 您是否可以通过其他服务连接到承载Adobe Campaign的服务器？

      通过SSH或任何其他方式连接到服务器。 如果这不可能，则您的主机公司会出现问题。 联系系统管理员。

1. **检查Web服务器端** (IIS/apache/etc)

   * Web服务器是否响应？

      使用Web浏览器连接到Adobe Campaign服务器访问URL: **http://`<urlserver>`**. 如果它没有响应，则Web服务器在计算机上停止。 请与主机公司的系统管理员联系以重新启动该服务。

   * Adobe Campaign是否已正确集成？

      登录到： **http:///`<urlserver>`/r/test** URL。 服务器应返回以下类型的消息

      ```
      <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='<hostname>' localHost='<server>'/>
      ```

      如果未获得此结果，请检查Web服务器配置是否考虑了集成。

1. **在Adobe Campaign端进行检查**

   * Adobe Campaign web模块是否已启动？

      连接到以下URL: **http://`<URLSERVER>`/nl/jsp/logon.jsp**

      * 如果您获得Tomcat java错误：

         JAVA集成是否正确执行？ Adobe Campaign需要SUN JDK。

         它集成在文件/nl6/customer.sh **`[path of application]`中&#x200B;**

      * 如果您获得空白页面：

         Adobe Campaign web模块是否已启动？ 您应当获得：

         ```
         nlserver pdump
         HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
         [...]
         web@default (27515) - 55.2 Mb
         [...]
         ```

      * 否则，请使用以下命令重新启动它：

         ```
         nlserver start web
         ```
>[!NOTE]
>
>如果您在列出Adobe Campaign模块时获得以下类型的响应： **nlserver pdump**
>HH:MM:SS > Adobe Campaign Classic(7.X YY.R内部版本XXX@SHA1),DD/MM/YYYY，无任务您必须重新启动整个Adobe Campaign应用程序。 为此，请使用以下命令：**nlserver watchdog -svc -noconsole **
