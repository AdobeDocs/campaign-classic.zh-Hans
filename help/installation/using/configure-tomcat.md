---
solution: Campaign Classic
product: campaign
title: 活动 Tomcat配置
description: 活动 Tomcat配置
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 8ab0aab42accbd1253d53e8133f5af0a38c724ea
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# 配置Apache Tomcat {#configuring-tomcat}

Adobe Campaign使用名为Apache Tomcat **的**&#x200B;嵌入式Web Servlet处理应用程序与任何外部接口（包括客户端控制台、跟踪的URL链接、SOAP调用等）之间的HTTP/HTTPS请求。 对于任何面向外部的Adobe Campaign实例，通常在此之前有一个外部Web服务器（通常是IIS或Apache）。

了解有关活动中的Tomcat以及如何在[此页](../../production/using/locate-tomcat-version.md)中找到Tomcat版本的更多信息。

>[!NOTE]
>
>此过程仅限于&#x200B;**内部部署**&#x200B;部署。


## Apache Tomcat {#default-port-for-tomcat}的默认端口

当Tomcat服务器的8080侦听端口已忙于配置所需的其他应用程序时，您需要将8080端口替换为免费端口（例如8090）。 要更改它，请编辑保存在Adobe Campaign安装文件夹&#x200B;**/tomcat-8/conf**&#x200B;目录中的&#x200B;**server.xml**&#x200B;文件。

然后修改JSP中继页的端口。 为此，请更改保存在Adobe Campaign安装目录&#x200B;**/conf**&#x200B;目录中的&#x200B;**serverConf.xml**&#x200B;文件。

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## 映射Apache Tomcat {#mapping-a-folder-in-tomcat}中的文件夹

要定义客户特定设置，可在&#x200B;**/tomcat-8/conf**&#x200B;文件夹中创建&#x200B;**user_上下文s.xml**&#x200B;文件，该文件中还包含&#x200B;**上下文.xml**&#x200B;文件。

此文件将包含以下类型的信息：

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

如有必要，可以在服务器端重现此操作。
