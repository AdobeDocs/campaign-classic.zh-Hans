---
solution: Campaign Classic
product: campaign
title: 安装客户端控制台
description: 了解如何安装客户端控制台
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 7%

---


# 安装活动客户端控制台{#installing-the-client-console}

活动客户端控制台是一个富客户端，它允许您连接到活动应用服务器。

在开始之前，您需要检查活动 [兼容性表](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)，获取活动服务器URL和用户凭据。

>[!CAUTION]
>
>活动客户端控制台和活动应用服务器必须在同一产品版本上运行。 Adobe还建议使用同一产品版本。

## 下载控制台{#download-the-client-console}

要下载并安装Adobe Campaign客户端控制台，请按照以下步骤操作：

1. 打开Web浏览器，并从以下地址下载控制台：

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. 在标识窗口中，输入您的登录名和口令。

   ![](assets/s_ncs_install_setup_download01.png)

   如有必要，请使用在实例创建过程中定义的内部帐户的凭据。

1. 单击安 **[!UICONTROL Download]** 装页面上的链接。
1. 下载并保存客户端安装文件。
1. 在Windows上的计算机上执行下载的文件：安装开始。 根据您的Adobe Campaign版本，客户 **端控制台的默认安装路径为$PROGRAMFILES$/Adobe/Adobe Campaign ClassicvX客户端**，其中“X”为“6”或“7”。

>[!NOTE]
>
>在Windows上，您可以直 **接从Windows服务** 器上的目录启动nlclient.exe文件，其 `[INSTALL]/bin``[INSTALL]` 中是Adobe Campaign安装文件夹的访问路径。

## 创建连接{#create-the-connection}

安装客户端控制台后，请按照以下步骤创建与应用程序服务器的连接：

1. 从开始组的“窗 **[!UICONTROL Start]** 口”菜单Adobe Campaign **控制** 台。

1. 单击凭据字段右上角的链接以访问连接配置窗口。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 单 **[!UICONTROL Add > Connection]** 击并输入Adobe Campaign应用程序服务器的标签和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 通过URL指定与Adobe Campaign应用程序服务器的连接。 使用计算机的DNS或别名，或您的IP地址。

   例如，您可以使用类 [`https://<machine>.<domain>.com`](https://myserver.adobe.com) 型URL。

1. 如果为您的组织配置了AdobeIMS，请选中此选项 **[!UICONTROL Connect with an Adobe ID]**

1. Click **[!UICONTROL Ok]** to save your settings.

例如，您可以根据需要添加任意数量的连接以连接到测试、舞台和生产环境。

>[!NOTE]
>
>The **[!UICONTROL Add]** button lets you create **[!UICONTROL folders]** to organize all your connections. 只需将每个连接拖放到某个文件夹中。

## 登录到Adobe Campaign

要登录到现有实例，请按照以下步骤操作：

1. 从开始组的“窗 **[!UICONTROL Start]** 口”菜单Adobe Campaign **控制** 台。

1. 单击凭据字段右上角的链接以访问连接配置窗口。

1. 选择您需要登录的活动实例。

1. 单击 **[!UICONTROL Ok]**

1. 输入用户登录凭据并单击 **[!UICONTROL Log in]**

**相关主题**

* [创建实例并登陆](../../installation/using/creating-an-instance-and-logging-on.md).
* [兼容性矩阵](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)
* [安装和设置Adobe Campaign客户端](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/getting-started/install-and-setup-the-adobe-campaign-client.html) （视频）
