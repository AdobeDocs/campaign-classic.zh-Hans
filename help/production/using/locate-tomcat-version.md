---
product: campaign
title: 在Adobe Campaign中找到Tomcat版本
description: 了解如何确定Adobe Campaign实例中使用的嵌入式Tomcat Web Servlet的当前版本
feature: Monitoring
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: fd4a815bca23b94590012c4883cfaa9c29b6f118
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# 找到Tomcat版本{#locate-tomcat-version}

Adobe Campaign使用名为Apache Tomcat **的**&#x200B;嵌入式Web servlet处理应用程序和任何外部接口(包括客户端控制台、跟踪的URL链接、SOAP调用等)之间的HTTP/HTTPS请求。 对于任何面向外部的Adobe Campaign实例，它前面通常有一个外部Web服务器（通常是IIS或Apache）。

请按照以下步骤查找&#x200B;**Campaign Classic内部部署实例**&#x200B;中使用的Tomcat的确切版本，以帮助解决问题。

## Adobe Campaign中使用的Tomcat

Tomcat在Java上运行，需要安装JDK。 有关详细信息，请参阅[Campaign兼容性矩阵](../../rn/using/compatibility-matrix.md)部分中的Java开发工具包(JDK)。

Adobe Campaign中使用的Tomcat是一个自定义的嵌入版本，它没有使用Tomcat的完整正式发行版本的所有功能，并且可能不会遭受完整版本的所有漏洞。 Tomcat也不应该向外部Internet公开，并且公开的任何Adobe Campaign实例都应该具有外部Web服务器（IIS、Apache等） 在Tomcat前保护它。

Tomcat嵌入式版本的新版本或升级版本仅随Adobe Campaign本身的新内部版本一起发布，而不会作为Adobe Campaign内部版本之外的单独修补程序发布。

>[!AVAILABILITY]
>
>
>* 从Campaign v7.4.1开始，Tomcat 10.1是默认版本。
>
>* Adobe Campaign Classic不使用WebSocket和HTTP2协议。
>


## 如何查找嵌入的Tomcat的版本

要在Adobe Campaign的实例中查找嵌入式Tomcat的版本，请执行以下步骤。

>[!NOTE]
>
>您必须有权访问您需要检查的Adobe Campaign服务器上的文件。 下面描述的过程仅适用于&#x200B;**内部部署托管模型**。

1. 导航到Adobe Campaign安装文件夹中的&#x200B;*\tomcat-11\lib*&#x200B;子文件夹(例如，Windows中的&#x200B;*C:\Program Files\ [Installation_folder]*&#x200B;或Linux中的&#x200B;*/usr/local/neolane/nl6*)。

1. 将文件&#x200B;*catalina.jar*&#x200B;复制到外部临时文件夹（例如，桌面），并将扩展名从.jar重命名为.zip。

1. 解压缩复制的文件。 这会生成许多子文件夹和文件。

1. 在解压缩的文件/文件夹中，使用文本编辑器打开或读取以下包含的文件： *org/apache/catalina/util/ServerInfo.properties*。 您可能需要添加.txt扩展名以方便使用文本编辑器打开。

1. 完成后，如果该文件位于服务器计算机上，请删除您创建的临时文件。

例如，Adobe Campaign的&#x200B;*ServerInfo.properties*&#x200B;文件包含以下信息，表示Tomcat v11.X：

*`server.info=Apache Tomcat/11.X`*

*`server.number=A.B.X.Y`*

*`server.built=MM DD YYY HH:MM:SS`*

一旦您能够建立特定实例中使用的Tomcat的确切版本，它可能会帮助您排除与Tomcat相关的问题。

>[!NOTE]
>
>嵌入式Tomcat的主要版本只有在Adobe Campaign的主要版本发生更改时才会升级（尽管官方可能不再支持旧版本，但由于某些客户仍在运行这些版本，这些信息可能会很有用）。
>

