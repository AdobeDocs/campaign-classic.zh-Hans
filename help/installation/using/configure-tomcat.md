---
product: campaign
title: Campaign Tomcat配置
description: Campaign Tomcat配置
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf,b4a422b4-4b8b-4883-8d74-0dccda4a5ef3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# 配置Apache Tomcat {#configuring-tomcat}

![](../../assets/v7-only.svg)

Adobe Campaign使用名为Apache Tomcat **的**&#x200B;嵌入式Web Servlet来处理应用程序与任何外部接口（包括客户端控制台、跟踪的URL链接、SOAP调用等）之间的HTTP/HTTPS请求。 对于任何面向外部的Adobe Campaign实例，通常会在其前面显示外部Web服务器（通常是IIS或Apache）。

进一步了解Campaign中的Tomcat，以及如何在[此页面](../../production/using/locate-tomcat-version.md)中找到Tomcat版本。

>[!NOTE]
>
>此过程仅限于&#x200B;**on-premise**&#x200B;部署。

## Apache Tomcat的默认端口 {#default-port-for-tomcat}

当Tomcat服务器的8080侦听端口已忙于配置所需的其他应用程序时，您需要将8080端口替换为免费端口（例如8090）。 要更改该文件，请编辑保存在Adobe Campaign安装文件夹&#x200B;**/tomcat-8/conf**&#x200B;目录中的&#x200B;**server.xml**&#x200B;文件。

然后修改JSP中继页的端口。 为此，请更改保存在Adobe Campaign安装目录&#x200B;**/conf**&#x200B;目录中的&#x200B;**serverConf.xml**&#x200B;文件。

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## 在Apache Tomcat中映射文件夹 {#mapping-a-folder-in-tomcat}

要定义客户特定的设置，可以在&#x200B;**/tomcat-8/conf**&#x200B;文件夹中创建&#x200B;**user_contexts.xml**&#x200B;文件，该文件还包含&#x200B;**contexts.xml**&#x200B;文件。

此文件将包含以下类型的信息：

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

如有必要，可以在服务器端重现此操作。
