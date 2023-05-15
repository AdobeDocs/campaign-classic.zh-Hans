---
product: campaign
title: 在Adobe Campaign中找到Tomcat版本
description: 了解如何查找在Adobe Campaign实例中使用的嵌入式Tomcat Web Servlet的当前版本
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 76411b29-d300-4aaa-8d3b-d8ff74c3ce93
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# 找到Tomcat版本{#locate-tomcat-version}



Adobe Campaign使用 **名为Apache Tomcat的嵌入式Web Servlet** 处理应用程序与任何外部接口（包括客户端控制台、跟踪的URL链接、SOAP调用等）之间的HTTP/HTTPS请求。 对于任何面向外部的Adobe Campaign实例，通常会在其前面显示外部Web服务器（通常是IIS或Apache）。

请按照以下步骤操作，以了解 **Campaign Classic内部部署实例** 以帮助进行问题故障诊断。

## Tomcat在Adobe Campaign中使用

Tomcat在Java上运行，需要安装JDK。 有关更多信息，请参阅 [Campaign兼容性矩阵](../../rn/using/compatibility-matrix.md) 中。

Adobe Campaign中使用的Tomcat是一个自定义的嵌入式版本，它没有使用Tomcat完整（通常可用）版本的所有功能，并且可能不会遭受完整版本的所有漏洞。 Tomcat也不应暴露在外部Internet中，任何公开的Adobe Campaign实例都应具有外部Web服务器（IIS、Apache等） 来保护它。

Tomcat嵌入版本的新版本或升级版本仅随Adobe Campaign本身的新内部版本一起发布，而不作为Adobe Campaign内部版本以外的单独修补程序发布。

## 如何查找嵌入式Tomcat的版本

要在Adobe Campaign实例中找到嵌入的Tomcat版本，请执行以下步骤。

>[!NOTE]
>
>您必须有权访问Adobe Campaign服务器上需要检查的文件。 下述程序仅适用于 **内部部署托管模型**.

1. 导航到 *\tomcat-7\lib* Adobe Campaign安装文件夹中的子文件夹(例如， *C:\Program Files\ [安装文件夹]* 或 */usr/local/neolane/nl6* 在Linux中)。

   如果您使用Tomcat v6运行旧版Adobe Campaign，请使用 *\tomcat-6\lib*.

1. 复制文件 *catalina.jar* 到外部临时文件夹（例如，您的桌面），并将扩展名从.jar重命名为.zip。

1. 解压缩复制的文件。 它会生成许多子文件夹和文件。

1. 在解压缩的文件/文件夹中，使用文本编辑器打开或读取以下包含的文件： *org/apache/catalina/util/ServerInfo.properties*. 您可能需要添加.txt扩展名，以便使用文本编辑器打开。

1. 完成后，如果它位于服务器计算机上，请删除您创建的临时文件。

例如， *ServerInfo.properties* Adobe Campaign的文件将包含以下信息，指示Tomcat v8.5.X:

*server.info=Apache Tomcat/8.5.X*

*server.number=8.5.X.Y*

*server.built=MM DD YYY HH:MM:SS*

在您能够确定特定实例中使用的Tomcat的确切版本后，它可能有助于您对与Tomcat相关的问题进行故障诊断。

>[!NOTE]
>
>仅当主要版本的Adobe Campaign发生更改时，才会升级嵌入式Tomcat的主要版本（尽管旧版本可能不再得到官方支持，但该信息可能会很有用，因为某些客户可能仍在运行这些版本）。
>
>例如，Adobe Campaign v6.02将始终使用Tomcat v6.x。
