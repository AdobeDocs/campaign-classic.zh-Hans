---
product: campaign
title: Campaign Tomcat配置
description: Campaign Tomcat配置
feature: Installation, Instance Settings
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: a2126458-2ae5-47c6-ad13-925f0e067ecf
source-git-commit: f032ed3bdc0b402c8281bc34e6cb29f3c575aaf9
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 1%

---

# 配置Apache Tomcat {#configuring-tomcat}

Adobe Campaign使用 **称为Apache Tomcat的嵌入式Web servlet** 在应用程序和任何外部界面（包括客户端控制台、跟踪的URL链接、SOAP调用等）之间处理HTTP/HTTPS请求。 对于任何面向外部的Adobe Campaign实例，它前面通常有一个外部Web服务器（通常是IIS或Apache）。

详细了解Campaign中的Tomcat以及如何在中找到您的Tomcat版本 [此页面](../../production/using/locate-tomcat-version.md).

>[!AVAILABILITY]
>
> 从v7.4.1开始，Tomcat 10.1是默认版本。
>


## Apache Tomcat的默认端口 {#default-port-for-tomcat}


>[!NOTE]
>
>此过程仅限于 **内部部署** 部署。
>

当Tomcat服务器的8080侦听端口已在使用您的配置所需的其他应用程序时，您需要将8080端口替换为空闲端口（例如8090）。 要更改它，请编辑 **server.xml** 文件保存在 **/tomcat-X/conf** Adobe Campaign安装文件夹的目录。

然后修改JSP中继页的端口。 为此，请更改 **serverConf.xml** 文件保存在 **/conf** Adobe Campaign安装目录的目录。

```xml
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

## 在Apache Tomcat中映射文件夹 {#mapping-a-folder-in-tomcat}


>[!NOTE]
>
>此过程仅限于 **内部部署** 部署。
>

要定义特定于客户的设置，您可以创建 **user_contexts.xml** 中的文件 **/tomcat-X/conf** 文件夹，其中还包含 **contexts.xml** 文件。

此文件将包含以下类型的信息：

```xml
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

如有必要，可以在服务器端重现此操作。

## 隐藏Tomcat错误报告 {#hide-tomcat-error-report}


>[!NOTE]
>
>此过程仅限于 **内部部署** 部署。
>
>从Campaign v7.4.1开始，不再需要此更改。
>

出于安全原因，我们强烈建议您隐藏Tomcat错误报告。 执行以下步骤：

1. 打开 **server.xml** 文件位于 **/tomcat-X/conf** Adobe Campaign安装文件夹的目录：  `/usr/local/neolane/nl6/tomcat-X/conf`
1. 在所有现有上下文元素后添加以下元素：

   ```xml
   <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false"/>
   ```

1. 重新启动nlserver和Apache Web Server。
