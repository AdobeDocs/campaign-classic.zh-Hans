---
product: campaign
title: 在Adobe Campaign中找到Tomcat版本
description: 了解如何查找在Adobe Campaign实例中使用的嵌入式Tomcat Web Servlet的当前版本。
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# 找到Tomcat版本{#locate-tomcat-version}

Adobe Campaign使用名为Apache Tomcat **的**&#x200B;嵌入式Web Servlet来处理应用程序与任何外部接口（包括客户端控制台、跟踪的URL链接、SOAP调用等）之间的HTTP/HTTPS请求。 对于任何面向外部的Adobe Campaign实例，通常会在其前面显示外部Web服务器（通常是IIS或Apache）。

请按照以下步骤查找&#x200B;**Campaign Classic内部部署实例**&#x200B;中使用的Tomcat的确切版本，以帮助对问题进行故障诊断。

## Tomcat在Adobe Campaign中使用

Tomcat在Java上运行，需要安装JDK。 有关更多信息，请参阅[Campaign兼容性矩阵](../../rn/using/compatibility-matrix.md)部分中的Java开发工具包(JDK)。

Adobe Campaign中使用的Tomcat是一个自定义的嵌入式版本，它没有使用Tomcat完整（通常可用）版本的所有功能，并且可能不会遭受完整版本的所有漏洞。 Tomcat也不应暴露在外部Internet中，任何公开的Adobe Campaign实例都应具有外部Web服务器（IIS、Apache等） 来保护它。

Tomcat嵌入版本的新版本或升级版本仅随Adobe Campaign本身的新内部版本一起发布，而不作为Adobe Campaign内部版本以外的单独修补程序发布。

## 如何查找嵌入式Tomcat的版本

要在Adobe Campaign实例中找到嵌入的Tomcat版本，请执行以下步骤。

>[!NOTE]
>
>您必须有权访问Adobe Campaign服务器上需要检查的文件。 下面描述的过程仅适用于&#x200B;**内部部署托管模型**。

1. 导航到Adobe Campaign安装文件夹中的&#x200B;*\tomcat-7\lib*&#x200B;子文件夹(例如，在Windows中，导航到&#x200B;*C:\Program Files\ [Installation_folder]*，或在Linux中，导航到&#x200B;*/usr/local/neolane/nl6*)。

   如果您使用Tomcat v6运行旧版Adobe Campaign，请使用&#x200B;*\tomcat-6\lib*。

1. 将文件&#x200B;*catalina.jar*&#x200B;复制到外部临时文件夹（例如，您的桌面）中，并将扩展名从.jar重命名为.zip。

1. 解压缩复制的文件。 它会生成许多子文件夹和文件。

1. 在解压缩的文件/文件夹中，使用文本编辑器打开或读取以下包含的文件：*org/apache/catalina/util/ServerInfo.properties*。 您可能需要添加.txt扩展名，以便使用文本编辑器打开。

1. 完成后，如果它位于服务器计算机上，请删除您创建的临时文件。

例如，Adobe Campaign的&#x200B;*ServerInfo.properties*&#x200B;文件将包含以下信息，指示Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.built=MM DD YYY HH:MM:SS*

在您能够确定特定实例中使用的Tomcat的确切版本后，它可能有助于您对与Tomcat相关的问题进行故障诊断。

>[!NOTE]
>
>仅当主要版本的Adobe Campaign发生更改时，才会升级嵌入式Tomcat的主要版本（尽管旧版本可能不再得到官方支持，但该信息可能会很有用，因为某些客户可能仍在运行这些版本）。
>
>例如，Adobe Campaign v6.02将始终使用Tomcat v6.x。
