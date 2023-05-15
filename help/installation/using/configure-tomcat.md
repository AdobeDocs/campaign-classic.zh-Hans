---
product: campaign
title: Campaign Tomcat配置
description: Campaign Tomcat配置
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# 配置Apache Tomcat {#configuring-tomcat}



Adobe Campaign使用 **名为Apache Tomcat的嵌入式Web Servlet** 处理应用程序与任何外部接口（包括客户端控制台、跟踪的URL链接、SOAP调用等）之间的HTTP/HTTPS请求。 对于任何面向外部的Adobe Campaign实例，通常会在其前面显示外部Web服务器（通常是IIS或Apache）。

进一步了解Campaign中的Tomcat以及如何在 [本页](../../production/using/locate-tomcat-version.md).

>[!NOTE]
>
>此过程仅限于 **内部部署** 部署。

## Apache Tomcat的默认端口 {#default-port-for-tomcat}

当Tomcat服务器的8080侦听端口已忙于配置所需的其他应用程序时，您需要将8080端口替换为免费端口（例如8090）。 要更改它，请编辑 **server.xml** 文件保存在 **/tomcat-8/conf** Adobe Campaign安装文件夹的目录。

然后修改JSP中继页的端口。 为此，请更改 **serverConf.xml** 文件保存在 **/conf** Adobe Campaign安装目录的目录。

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## 在Apache Tomcat中映射文件夹 {#mapping-a-folder-in-tomcat}

要定义客户特定的设置，您可以创建 **user_contexts.xml** 文件 **/tomcat-8/conf** 文件夹，其中还包含 **contexts.xml** 文件。

此文件将包含以下类型的信息：

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

如有必要，可以在服务器端重现此操作。

## 隐藏Tomcat错误报告 {#hide-tomcat-error-report}

出于安全考虑，我们强烈建议您隐藏Tomcat错误报告。 以下是步骤。

1. 打开 **server.xml** 文件位于 **/tomcat-8/conf** Adobe Campaign安装文件夹的目录：  `/usr/local/neolane/nl6/tomcat-8/conf`
1. 在所有现有上下文元素之后的底部添加以下元素：

   ```
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. 重新启动nlserver和Apache Web服务器。
