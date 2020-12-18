---
solution: Campaign Classic
product: campaign
title: 安装客户端控制台
description: 了解如何安装客户端控制台
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: cea4a26935312b1cb119a3fa671af7bf00788fe9
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 8%

---


# 安装活动客户端控制台{#installing-the-client-console}

活动客户端控制台是一个富客户端，它允许您连接到活动应用服务器。

在开始之前，您需要检查活动[兼容性矩阵](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)，获取活动服务器URL和用户凭据。

>[!CAUTION]
>
>活动客户端控制台和活动应用服务器必须在同一产品版本上运行。 Adobe还建议使用同一产品版本。

![](assets/do-not-localize/how-to-video.png) 了解如何在视频中安装和设置Adobe Campaign客 [户端](#video)

## 下载控制台{#download-the-client-console}

要下载并安装Adobe Campaign客户端控制台，请按照以下步骤操作：

1. 打开Web浏览器，并从以下地址下载控制台：

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. 在标识窗口中，输入您的登录名和口令。

   ![](assets/s_ncs_install_setup_download01.png)

   如有必要，请使用在实例创建过程中定义的内部帐户的凭据。

1. 单击安装页上的&#x200B;**[!UICONTROL Download]**&#x200B;链接。
1. 下载并保存客户端安装文件。
1. 在Windows上的计算机上执行下载的文件：安装开始。 根据您的Adobe Campaign版本，客户端控制台的默认安装路径为&#x200B;**$PROGRAMFILES$/Adobe/Adobe Campaign ClassicvX客户端**，其中“X”为“6”或“7”。

>[!NOTE]
>
>在Windows上，您可以直接从Windows服务器上的`[INSTALL]/bin`目录启动&#x200B;**nlclient.exe**&#x200B;文件，其中`[INSTALL]`是Adobe Campaign安装文件夹的访问路径。

## 创建连接{#create-the-connection}

安装客户端控制台后，请按照以下步骤创建与应用程序服务器的连接：

1. 从&#x200B;**Adobe Campaign**&#x200B;项目组的Windows **[!UICONTROL Start]**&#x200B;菜单开始控制台。

1. 单击凭据字段右上角的链接以访问连接配置窗口。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 单击&#x200B;**[!UICONTROL Add > Connection]**&#x200B;并输入Adobe Campaign应用程序服务器的标签和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 通过URL指定与Adobe Campaign应用程序服务器的连接。 使用计算机的DNS或别名，或您的IP地址。

   例如，您可以使用[`https://<machine>.<domain>.com`](https://myserver.adobe.com)类型URL。

1. 如果为您的组织配置了AdobeIMS，请选中选项&#x200B;**[!UICONTROL Connect with an Adobe ID]**

1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;以保存设置。

例如，您可以根据需要添加任意数量的连接以连接到测试、舞台和生产环境。

>[!NOTE]
>
>通过&#x200B;**[!UICONTROL Add]**&#x200B;按钮可创建&#x200B;**[!UICONTROL folders]**&#x200B;来组织所有连接。 只需将每个连接拖放到某个文件夹中。

## 登录到Adobe Campaign

要登录到现有实例，请按照以下步骤操作：

1. 从&#x200B;**Adobe Campaign**&#x200B;项目组的Windows **[!UICONTROL Start]**&#x200B;菜单开始控制台。

1. 单击凭据字段右上角的链接以访问连接配置窗口。

1. 选择您需要登录的活动实例。

1. 单击 **[!UICONTROL Ok]**

1. 输入用户登录凭据，然后单击&#x200B;**[!UICONTROL Log in]**

**相关主题**

* [创建实例并登陆](../../installation/using/creating-an-instance-and-logging-on.md).
* [兼容性矩阵](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

## 教程视频

此视频演示如何安装和设置Adobe Campaign客户端。

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

此处[提供其他Campaign Classic操作方法视频。](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)
