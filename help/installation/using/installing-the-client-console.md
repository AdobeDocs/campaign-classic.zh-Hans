---
product: campaign
title: 安装客户端控制台
description: 了解如何安装客户端控制台
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1118'
ht-degree: 4%

---

# 安装和更新Campaign客户端控制台{#installing-the-client-console}



Campaign客户端控制台是一个富客户端，可让您连接到Campaign应用程序服务器。

在开始安装客户端控制台之前，您需要：

* 在 [兼容性矩阵](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* 获取Campaign服务器URL
* 获取用户凭据
* 在您的系统上安装Microsoft Edge Webview2运行时(从Campaign Classic7.3内部版本)。 [了解详情](#webview)

安装或更新客户端控制台的过程因您实施的Adobe Campaign Classic而异。
请查看以下详细信息，以了解实施所需的内容。

![](assets/do-not-localize/how-to-video.png) 了解如何在 [视频](#video)

>[!CAUTION]
>
>Campaign客户端控制台和Campaign应用程序服务器必须运行 **在同一产品版本上**. Adobe还强烈建议使用 **同一产品版本**. 了解如何在 [此部分](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Microsoft Edge Webview2运行时安装 {#webview}

从Campaign Classic7.3内部版本开始，任何控制台安装都需要安装Microsoft Edge Webview 2运行时。

Web View默认作为Windows 11操作系统的一部分安装。 如果系统上尚不存在Campaign Classic控制台安装程序，将提示您从下载它 [Microsoft开发人员网站](http://www.adobe.com/go/acc-ms-webview2-runtime-download_cn). 请注意，下载链接在Internet Explorer 11浏览器上不起作用，因为Microsoft已弃用其支持。 确保使用其他浏览器访问该链接。

## Adobe托管的实施 {#hosted-customers}

作为托管客户，您有两个选项可用来安装或更新客户端控制台：

1. Adobe可以直接部署。 更新控制台后，系统将在弹出窗口中提示用户下载最新的客户端控制台版本。

1. 您可以从下载到客户端控制台 [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html)

   **用户需要管理员访问权限才能完成更新。 如果用户没有管理员权限，则系统管理员需要部署到所有客户端控制台**

## 混合和内部部署实施 {#hybrid-onprem-customers}

要使Adobe Campaign用户能够登录到您创建和配置的实例，他们需要使用客户端控制台。

### 使控制台可供用户使用 {#make-console-available}

当用于启动Adobe Campaign应用程序服务器(nlserver web)的计算机从客户端控制台接收用户连接时，您可以将其配置为通过HTML界面使Adobe Campaign富客户端的设置程序可用。 当客户端控制台有新版本可用时，系统会邀请用户在启动其客户端控制台时下载它。

为此，您必须：

1. 选择包含控制台安装程序的包。

   对于v7，此文件称为setup-client-7.X.XXXX.exe ，对于v6.1，此文件称为setup-client-6.X.XXXX.exe ，其中X是Adobe Campaign的子版本，XXXX是内部版本号。

1. 将此包复制并粘贴到Adobe Campaign安装文件夹（在混合安装的营销服务器上）的/datakit/nl/eng/jsp下。

1. 启动Adobe Campaign服务器。


### 不再提出此问题选项

Adobe建议将选项保留为 **[!UICONTROL No longer ask this question]** 取消选中，以确保当有新版本的控制台可用时，所有用户都会收到警报。  如果选择此选项，则用户将不会获悉新的可用版本。

如果 **[!UICONTROL No longer ask this question]**  已选择，您可以重置此提示。 只有能够编辑Windows注册表的系统管理员才应进行以下更改：

1. 使用打开注册表编辑器 **regedit** 命令 **[!UICONTROL Start > Run]** 菜单。

1. 搜索节点并展开该节点。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 删除 **confDewildedUpgrade** 登录并关闭注册表编辑器。

>[!NOTE]
>
>如果您将更新的控制台应用于现有实施，用户将自动收到更新其客户端控制台的提示。 如果您是首次实施Campaign，则用户将需要下载控制台。 有关这两个选项的详细信息，请参阅下文

### 为现有实施更新控制台{#update-the-client-console}

控制台在Campaign服务器文件夹中可用后，系统会在弹出窗口中提示用户下载最新的客户端控制台版本。

**用户需要管理员访问权限才能完成更新。 如果用户没有管理员权限，则系统管理员需要部署到所有客户端控制台**


### 下载用于新实施的控制台{#download-the-client-console}

用户现在应按照以下步骤下载并安装控制台：

1. 打开Web浏览器并从以下地址下载控制台：

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`.

1. 在标识窗口中，输入登录名和密码。

   ![](assets/s_ncs_install_setup_download01.png)

   如有必要，请使用在实例创建过程中定义的内部帐户的凭据。

1. 单击 **[!UICONTROL Download]** 链接。
1. 下载并保存客户端设置文件。
1. 在Windows的计算机上执行下载的文件：安装开始。 客户端控制台的默认安装路径为 **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX客户端**，其中“X”是“6”或“7”，具体取决于您的Adobe Campaign版本。

### 创建连接 — 仅首次用户{#create-the-connection}

安装客户端控制台后，请按照以下步骤创建与应用程序服务器的连接：

1. 从Windows启动控制台 **[!UICONTROL Start]** 菜单中 **Adobe Campaign** 项目组。

1. 单击凭据字段右上角的链接以访问连接配置窗口。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 单击 **[!UICONTROL Add > Connection]** 并输入Adobe Campaign应用程序服务器的标签和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 通过URL指定与Adobe Campaign应用程序服务器的连接。 使用DNS或计算机的别名，或您的IP地址。

   例如，您可以使用 [`https://<machine>.<domain>.com`](https://myserver.adobe.com) 键入URL。

1. 如果为贵组织配置了Adobe IMS，请勾选选项 **[!UICONTROL Connect with an Adobe ID]**

1. 单击 **[!UICONTROL Ok]** 来保存设置。

您可以根据需要添加任意数量的连接，以连接到测试、暂存和生产环境等。

>[!NOTE]
>
>的 **[!UICONTROL Add]** 按钮 **[!UICONTROL folders]** 来组织你的所有联系。 只需将每个连接拖放到某个文件夹中。

### 登录Adobe Campaign

要登录到现有实例，请执行以下步骤：

1. 从Windows启动控制台 **[!UICONTROL Start]** 菜单中 **Adobe Campaign** 项目组。

1. 单击凭据字段右上角的链接以访问连接配置窗口。

1. 选择您需要登录的Campaign实例。

1. 单击 **[!UICONTROL Ok]**

1. 输入用户登录凭据并单击 **[!UICONTROL Log in]**

>[!NOTE]
>
>对于campaign classic 7.3内部版本，Adobe Campaign客户端控制台在代理身份验证期间可能两次请求获取代理凭据。 这是因为与Internet Explorer不同，Microsoft Edge Webview2未将代理凭据保存在缓存/密码存储区中。

**相关主题**

* [创建实例并登陆](../../installation/using/creating-an-instance-and-logging-on.md).
* [兼容性矩阵](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

## 教程视频

此视频演示如何安装和设置Adobe Campaign客户端。

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

提供了其他Campaign Classic操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).
