---
title: 安装客户端控制台
seo-title: 安装客户端控制台
description: 安装客户端控制台
seo-description: null
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: be590c6d993eecacf51736e3c3e415addae5c6bd

---


# 安装客户端控制台{#installing-the-client-console}

Adobe Campaign控制台安装过程详细如下。

在安装Adobe Campaign控制台之前，请检查兼容性列表中列出的 [先决条件](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

要安装Adobe Campaign控制台，请应用以下步骤：

1. 打开Web浏览器，然后从以下地址下载控制台：

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. 在标识窗口中，输入您的登录名和密码。

   ![](assets/s_ncs_install_setup_download01.png)

   如有必要，请使用在创建实例过程中定义的内部帐户的凭据。

1. 单击安 **[!UICONTROL Download]** 装页面上的链接。
1. 下载并保存客户端安装文件。
1. 在Windows上的计算机上执行下载的文件：将启动安装。 根据Adobe Campaign版本，客户端控制台的默认安装路径是 **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX客户端**，其中“X”为“6”或“7”。
1. 安装程序完成后，从Windows菜单(在 **[!UICONTROL Start]****** Adobe Campaign程序组中)启动控制台。

>[!NOTE]
>
>在Windows上，您可以直接从Windows服务器 **上的目录启动nlclient.exe文件，其中**`[INSTALL]/bin``[INSTALL]` 是Adobe Campaign安装文件夹的访问路径。\
>要创建新连接，请参阅 [创建实例并登录](../../installation/using/creating-an-instance-and-logging-on.md)。

