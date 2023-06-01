---
product: campaign
title: 安装客户端控制台
description: 了解如何安装客户端控制台
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: acfe0c4139671fc3df69ff434ba307aaaaf70676
workflow-type: tm+mt
source-wordcount: '1111'
ht-degree: 4%

---

# 安装和更新Campaign客户端控制台{#installing-the-client-console}



Campaign客户端控制台是一个富客户端，可用于连接到Campaign应用程序服务器。

在开始安装客户端控制台之前，您需要：

* 在中检查您的系统和工具与Adobe Campaign的兼容性 [兼容性矩阵](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* 获取Campaign服务器URL
* 获取您的用户凭据
* 在您的系统上安装Microsoft Edge Webview2运行时(来自Campaign Classic7.3内部版本)。 [了解详情](#webview)

安装或更新客户端控制台的过程因您实施的Adobe Campaign Classic而异。
请查看以下详细信息以了解实施所需的内容。

![](assets/do-not-localize/how-to-video.png) 了解如何在中安装和设置Adobe Campaign客户端 [视频](#video)

>[!CAUTION]
>
>必须运行Campaign客户端控制台和Campaign应用程序服务器 **在相同产品版本上**. Adobe还强烈建议使用 **相同的产品版本**. 了解如何在中检查您的Campaign客户端和服务器版本 [本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Microsoft Edge Webview2运行时安装 {#webview}

从Campaign Classic7.3内部版本开始，任何控制台安装都需要安装Microsoft Edge Webview 2运行时。

Web View默认作为Windows 11操作系统的一部分安装。 如果您的系统中不存在该程序，Campaign Classic控制台安装程序将提示您从以下位置下载它 [Microsoft开发人员网站](http://www.adobe.com/go/acc-ms-webview2-runtime-download_cn). 请注意，下载链接在Internet Explorer 11浏览器上不起作用，因为Microsoft已弃用其支持。 确保使用其他浏览器访问链接。

## Adobe托管的实施 {#hosted-customers}

作为托管客户，您可以通过两个选项来安装或更新客户端控制台：

1. Adobe可以直接部署。 更新控制台后，将提示用户在弹出窗口中下载最新的客户端控制台版本。

1. 您可以从以下位置下载到您的客户端控制台： [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html)

   **用户需要管理员访问权限才能完成更新。 如果用户没有管理权限，系统管理员需要部署到所有客户端控制台**

## 混合和内部部署实施 {#hybrid-onprem-customers}

为了让Adobe Campaign用户能够登录到您已创建和配置的实例，他们需要使用客户端控制台。

### 使控制台可供用户使用 {#make-console-available}

当用于启动Adobe Campaign应用程序服务器(nlserver web)的计算机收到来自客户端控制台的用户连接时，您可以将其配置为通过HTML界面提供Adobe Campaign富客户端的安装程序。 每当有新版本的客户端控制台可用时，都会邀请用户在启动其客户端控制台时下载该版本。

要实现此目的，您必须：

1. 选择包含控制台安装程序的软件包。

   此文件名为setup-client-7.X.XXXX.exe ，其中X是Adobe Campaign的子版本，XXXX是内部版本号。

1. 将此包复制并粘贴到/datakit/nl/eng/jsp下的Adobe Campaign安装文件夹（对于混合安装，位于Marketing Server上）中。

1. 启动Adobe Campaign服务器。


### 不再询问此问题选项

Adobe建议保留选项 **[!UICONTROL No longer ask this question]** 未选中，以确保当有新版本的控制台可用时，所有用户都会收到警报。  如果选择此选项，用户不会收到有关新可用版本的通知。

如果 **[!UICONTROL No longer ask this question]**  已选中，您可以重置此提示。 只有能够编辑Windows注册表的系统管理员才应该进行以下更改：

1. 使用打开注册表编辑器 **regedit** 命令 **[!UICONTROL Start > Run]** 菜单。

1. 搜索并展开节点。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 删除 **confAdvisedUpgrade** 输入并关闭注册表编辑器。

>[!NOTE]
>
>如果您将更新的控制台应用于现有实施，用户将自动收到更新其客户端控制台的提示。 如果您是首次实施Campaign，则用户需要下载控制台。 有关这两个选项的详细信息，请参阅下文

### 更新现有实施的控制台{#update-the-client-console}

控制台在Campaign服务器文件夹中可用后，将提示用户在弹出窗口中下载最新的客户端控制台版本。

**用户需要管理员访问权限才能完成更新。 如果用户没有管理权限，系统管理员需要部署到所有客户端控制台**


### 下载控制台以进行新实施{#download-the-client-console}

用户现在应按照以下步骤下载并安装控制台：

1. 打开Web浏览器，然后从以下地址下载控制台：

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`.

1. 在标识窗口中，输入登录名和密码。

   ![](assets/s_ncs_install_setup_download01.png)

   如有必要，请使用实例创建期间定义的内部帐户的凭据。

1. 单击 **[!UICONTROL Download]** 安装页面上的链接。
1. 下载并保存客户端设置文件。
1. 在Windows上的计算机上执行下载的文件：安装启动。 客户端控制台的默认安装路径为 **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX客户端**，其中，“X”是“6”或“7”(根据您的Adobe Campaign版本)。

### 创建连接 — 仅首次用户{#create-the-connection}

安装客户端控制台后，请按照以下步骤创建与应用程序服务器的连接：

1. 从Windows启动控制台 **[!UICONTROL Start]** 菜单，在 **Adobe Campaign** 项目群组。

1. 单击凭据字段右上角的链接以访问连接配置窗口。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 单击 **[!UICONTROL Add > Connection]** 并输入Adobe Campaign应用程序服务器的标签和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 通过URL指定与Adobe Campaign应用程序服务器的连接。 使用计算机的DNS或别名或IP地址。

   例如，您可以使用 [`https://<machine>.<domain>.com`](https://myserver.adobe.com) 键入URL。

1. 如果为贵组织配置了Adobe IMS，请勾选选项 **[!UICONTROL Connect with an Adobe ID]**

1. 单击 **[!UICONTROL Ok]** 以保存您的设置。

例如，您可以根据需要添加任意数量的连接，以连接到测试、暂存和生产环境。

>[!NOTE]
>
>此 **[!UICONTROL Add]** 按钮可让您创建 **[!UICONTROL folders]** 以组织所有连接。 只需将每个连接拖放到某个文件夹中。

### 登录到Adobe Campaign

要登录到现有实例，请执行以下步骤：

1. 从Windows启动控制台 **[!UICONTROL Start]** 菜单，在 **Adobe Campaign** 项目群组。

1. 单击凭据字段右上角的链接以访问连接配置窗口。

1. 选择您需要登录的Campaign实例。

1. 单击 **[!UICONTROL Ok]**

1. 输入用户登录凭据并单击 **[!UICONTROL Log in]**

>[!NOTE]
>
>对于campaign classic 7.3内部版本而言，Adobe Campaign客户端控制台可能会在代理身份验证期间询问代理凭据两次。 这是因为Microsoft Edge Webview2不像Internet Explorer那样将代理凭据保存在缓存/密码存储区。

**相关主题**

* [创建实例并登陆](../../installation/using/creating-an-instance-and-logging-on.md).
* [兼容性矩阵](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

## 教程视频

本视频说明如何安装和设置Adobe Campaign客户端。

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

提供了其他Campaign Classic操作方法视频 [此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans).
