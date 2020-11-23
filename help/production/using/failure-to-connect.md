---
solution: Campaign Classic
product: campaign
title: 连接失败
description: 连接失败
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 2%

---


# 连接失败{#failure-to-connect}

原因可能是多重的，并取决于各种上下文。

检查安全区域的常规配置。

>[!NOTE]
>
>有关配置安全区域的详细信息，请参 [阅此部分](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

检查以下信息：

1. **网络检查**

   * 您是否可以从计算机访问Internet?

      检查是否可以连接到Internet上的网站（例如）。 如果无法连接，则问题出在您的计算机上。 与系统管理员联系。

   * 是否可以通过其他服务连接到承载Adobe Campaign的服务器？

      通过SSH或任何其他方式连接到服务器。 如果这不可能，则主机公司有问题。 与系统管理员联系。

1. **检查Web服务器端** (IIS/apache/etc.)

   * Web服务器是否响应？

      使用Web浏览器连接到Adobe Campaign服务器访问URL: **//`<urlserver>`**。 如果它没有响应，则计算机上停止Web服务器。 请与主机公司的系统管理员联系以重新启动该服务。

   * Adobe Campaign是否已正确集成？

      登录到： **http(s):// `<urlserver>`//r/test** URL。 服务器应返回以下类型的消息

      ```
      <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='<hostname>' localHost='<server>'/>
      ```

      如果未获得此结果，请检查Web服务器配置中是否考虑了集成。

1. **检查Adobe Campaign**

   * Adobe CampaignWeb模块是否已启动？

      连接到以下URL: **/nl/jsp/logon.jsp`<URLSERVER>`**

      * 如果获得Tomcat Java错误：

         JAVA集成是否正确执行？ Adobe Campaign需要SUN JDK。

         它集成在文件/nl6/customer.sh **`[path of application]`中**

      * 如果您获得空白页面：

         Adobe CampaignWeb模块是否已启动？ 您应获得：

         ```
         nlserver pdump
         HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
         [...]
         web@default (27515) - 55.2 Mb
         [...]
         ```

      * 如果不是，请使用以下命令重新启动它：

         ```
         nlserver start web
         ```
>[!NOTE]
>
>如果在列表Adobe Campaign模块时获得以下类型的响应： **nlserver pdump**
>HH:MM:SS >Adobe Campaign Classic(7.X YY.R内部版本XXX@SHA1)的应用程序服务器：DD/MM/YYYY无任务。您必须重新启动整个Adobe Campaign应用程序。 为此，请使用以下命令：**nlserver watchdog -svc -noconsole **
