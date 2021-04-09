---
solution: Campaign Classic
product: campaign
title: 在Adobe Campaign中找到Tomcat版本
description: 了解如何找出用于Adobe Campaign实例的嵌入式Tomcat web servlet的当前版本。
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# 找到Tomcat版本{#locate-tomcat-version}

Adobe Campaign使用名为Apache Tomcat **的**&#x200B;嵌入式Web Servlet处理应用程序与任何外部接口（包括客户端控制台、跟踪的URL链接、SOAP调用等）之间的HTTP/HTTPS请求。 对于任何面向外部的Adobe Campaign实例，通常在此之前有一个外部Web服务器（通常是IIS或Apache）。

请按照以下步骤查找&#x200B;**Campaign Classic内部部署实例**&#x200B;中使用的Tomcat的确切版本，以帮助解决问题。

## 用于Adobe Campaign的Tomcat

Tomcat在Java上运行，需要安装JDK。 有关详细信息，请参阅[活动兼容性矩阵](../../rn/using/compatibility-matrix.md)部分中的Java开发工具包(JDK)。

Adobe Campaign中使用的Tomcat是一个自定义的嵌入式版本，它不使用Tomcat完整版一般可用的所有功能，并且可能不会受到完整版的所有漏洞的影响。 Tomcat也不应暴露在外部Internet，公开的任何Adobe Campaign实例都应具有外部Web服务器（IIS、Apache等） 来保护它。

Tomcat的嵌入式版本的新版本或升级版本仅随Adobe Campaign本身的新版本一起发布，而不是作为Adobe Campaign版本之外的单独修补程序发布。

## 如何定位嵌入式Tomcat的版本

要在Adobe Campaign实例中查找嵌入式Tomcat的版本，请执行以下步骤。

>[!NOTE]
>
>您必须有权访问要检查的Adobe Campaign服务器上的文件。 下面描述的过程仅适用于&#x200B;**内部部署托管模型**。

1. 导航到Adobe Campaign安装文件夹中的&#x200B;*\tomcat-7\lib*&#x200B;子文件夹(例如，Windows中的&#x200B;*C:\Program Files\ [Installation_folder]*，或Linux中的&#x200B;*/usr/local/neolane/nl6*)。

   如果您使用Tomcat v6运行旧版Adobe Campaign，请使用&#x200B;*\tomcat-6\lib*。

1. 将文件&#x200B;*catalina.jar*&#x200B;复制到外部临时文件夹（例如，您的桌面），然后将扩展名从.jar重命名为.zip。

1. 解压缩复制的文件。 它将生成许多子文件夹和文件。

1. 在解压缩的文件/文件夹中，使用文本编辑器打开或读取以下包含的文件：*org/apache/catalina/util/ServerInfo.properties*。 您可能需要添加.txt扩展名以便于使用文本编辑器打开。

1. 完成后，如果它位于服务器计算机上，请删除您创建的临时文件。

例如，用于Adobe Campaign的&#x200B;*ServerInfo.properties*&#x200B;文件将包含以下信息，指示Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.built=MM DDYYY HH:MM:SS*

一旦您能够确定特定实例中使用的Tomcat的确切版本，它可能会帮助您排除与Tomcat相关的问题。

>[!NOTE]
>
>仅当主要版本的Adobe Campaign发生更改时，才升级嵌入式Tomcat的主要版本（尽管旧版本可能不再得到正式支持，但由于某些客户可能仍在运行这些版本，因此该信息可能很有用）。
>
>例如，Adobe Campaign v6.02将始终使用Tomcat v6.x。
