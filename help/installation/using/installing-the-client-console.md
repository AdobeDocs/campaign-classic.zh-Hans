---
product: campaign
title: 安装客户端控制台
description: 了解如何安装客户端控制台
feature: Installation, Upgrade
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 2%

---

# 安装和更新Campaign客户端控制台{#installing-the-client-console}

Campaign客户端控制台是一个富客户端，可让您连接到Campaign应用程序服务器。

在开始安装客户端控制台之前，您需要：

* 在[兼容性矩阵](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)中检查您的系统和工具与Adobe Campaign的兼容性
* 获取Campaign服务器URL
* 获取您的用户凭据
* 在您的系统上安装Microsoft Edge Webview2运行时(来自Campaign Classic7.3内部版本号)。 [了解详情](#webview)

安装或更新客户端控制台的过程因您实施的Adobe Campaign Classic而异。
请查看以下详细信息以了解实施所需的内容。

![](assets/do-not-localize/how-to-video.png)在[视频](#video)中了解如何安装和设置Adobe Campaign客户端

>[!CAUTION]
>
>* Campaign客户端控制台和Campaign应用程序服务器必须在相同的产品版本&#x200B;**上运行**。 Adobe还强烈建议使用&#x200B;**相同的产品版本**。 在[本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何检查您的Campaign客户端和服务器版本。
>
>* 应仅允许目标用户访问安装控制台的安装文件夹，确保相应地限制写入权限。



## Microsoft Edge Webview2运行时安装 {#webview}

从Campaign Classic7.3内部版本开始，任何控制台安装都需要安装Microsoft Edge Webview 2运行时。

默认情况下，Web View作为Windows 11操作系统的一部分安装。 如果系统中不存在该程序，Campaign Classic控制台安装程序将提示您从[Microsoft开发人员网站](https://www.adobe.com/go/acc-ms-webview2-runtime-download_cn)下载它。 请注意，下载链接在Internet Explorer 11浏览器上不起作用，因为Microsoft已弃用其支持。 确保使用其他浏览器来访问该链接。

## Adobe托管的实施 {#hosted-customers}

作为托管客户，您有两个选项可用于安装或更新客户端控制台：

1. Adobe可以直接部署。 更新控制台后，将提示用户在弹出窗口中下载最新的客户端控制台版本。

1. 您可以从[软件分发](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html)下载到您的客户端控制台

   **用户需要管理员访问权限才能完成更新。 如果用户没有管理员权限，系统管理员需要部署到所有客户端控制台**

## 混合和内部部署实施 {#hybrid-onprem-customers}

为了让Adobe Campaign用户能够登录到您已创建和配置的实例，他们需要使用客户端控制台。

### 使用户能够使用该控制台 {#make-console-available}

当用于启动Adobe Campaign应用程序服务器(nlserver web)的计算机收到来自客户端控制台的用户连接时，您可以对其进行配置，以通过HTML界面提供Adobe Campaign富客户端的安装程序。 每当有新版本的客户端控制台可用时，都会邀请用户在启动其客户端控制台时下载该版本。

为此，您必须：

1. 选择包含控制台安装程序的软件包。

   此文件名为setup-client-7.X.XXXX.exe ，其中X是Adobe Campaign的子版本，XXXX是内部版本号。

1. 将此包复制并粘贴到/datakit/nl/eng/jsp下的Adobe Campaign安装文件夹（对于混合安装，位于营销服务器上）。

1. 启动Adobe Campaign服务器。


### 不再询问此问题选项

Adobe建议取消选择选项&#x200B;**[!UICONTROL No longer ask this question]**，以确保当有新版本的控制台可用时，所有用户都会收到警报。  如果选择此选项，则不会通知用户新的可用版本。

如果已选择&#x200B;**[!UICONTROL No longer ask this question]**，则可以重置此提示。 只有能够编辑Windows注册表的系统管理员才应该进行以下更改：

1. 使用&#x200B;**[!UICONTROL Start > Run]**&#x200B;菜单中的&#x200B;**regedit**&#x200B;命令打开注册表编辑器。

1. 搜索并展开节点。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 删除&#x200B;**confAdvisedUpgrade**&#x200B;条目并关闭注册表编辑器。

>[!NOTE]
>
>如果您将更新的控制台应用于现有实施，用户将自动收到更新其客户端控制台的提示。 如果您是首次实施Campaign，则用户需要下载控制台。 有关这两个选项的详细信息，请参见下文

### 更新现有实施的控制台{#update-the-client-console}

控制台在Campaign服务器文件夹中可用后，将提示用户在弹出窗口中下载最新的客户端控制台版本。

**用户需要管理员访问权限才能完成更新。 如果用户没有管理员权限，系统管理员需要部署到所有客户端控制台**


### 下载控制台以进行新实施{#download-the-client-console}

用户现在应按照以下步骤下载并安装控制台：

1. 打开Web浏览器，然后从以下地址下载控制台：

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`。

1. 在标识窗口中，输入登录名和密码。

   ![](assets/s_ncs_install_setup_download01.png)

   如有必要，请使用实例创建期间定义的内部帐户的凭据。

1. 单击安装页面上的&#x200B;**[!UICONTROL Download]**&#x200B;链接。
1. 下载并保存客户端设置文件。
1. 在Windows上的计算机上执行下载的文件：安装将启动。 客户端控制台的默认安装路径为&#x200B;**$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**，其中&#39;X&#39;为&#39;6&#39;或&#39;7&#39;(根据您的Adobe Campaign版本)。

### 创建连接 — 仅首次用户{#create-the-connection}

安装客户端控制台后，请按照以下步骤创建与应用程序服务器的连接：

1. 从&#x200B;**Adobe Campaign**&#x200B;程序组中的Windows **[!UICONTROL Start]**&#x200B;菜单启动控制台。

1. 单击凭据字段右上角的链接可访问连接配置窗口。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 单击&#x200B;**[!UICONTROL Add > Connection]**&#x200B;并输入Adobe Campaign应用程序服务器的标签和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 通过URL指定与Adobe Campaign应用程序服务器的连接。 使用计算机的DNS或别名或IP地址。

   例如，您可以使用`https://<machine>.<domain>.com`类型URL。

1. 如果为贵组织配置了Adobe IMS，请选中选项&#x200B;**[!UICONTROL Connect with an Adobe ID]**

1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;保存您的设置。

例如，您可以根据需要添加任意数量的连接，以连接到测试、暂存和生产环境。

>[!NOTE]
>
>通过&#x200B;**[!UICONTROL Add]**&#x200B;按钮可创建&#x200B;**[!UICONTROL folders]**&#x200B;以组织所有连接。 只需将每个连接拖放到某个文件夹中。

### 登录到Adobe Campaign

要登录到现有实例，请执行以下步骤：

1. 从&#x200B;**Adobe Campaign**&#x200B;程序组中的Windows **[!UICONTROL Start]**&#x200B;菜单启动控制台。

1. 单击凭据字段右上角的链接可访问连接配置窗口。

1. 选择您需要登录的Campaign实例。

1. 单击&#x200B;**[!UICONTROL Ok]**

1. 输入您的用户登录凭据并单击&#x200B;**[!UICONTROL Log in]**

>[!NOTE]
>
>对于campaign classic 7.3内部版本而言，Adobe Campaign客户端控制台可能会在代理身份验证期间请求两次代理凭据。 这是因为Microsoft Edge Webview2不像Internet Explorer那样将代理凭据保存在缓存/密码存储区。

**相关主题**

* [正在创建实例并登录](../../installation/using/creating-an-instance-and-logging-on.md)。
* [兼容性矩阵](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)

## 教程视频

本视频说明如何安装和设置Adobe Campaign客户端。

>[!VIDEO](https://video.tv.adobe.com/v/38266?quality=12&captions=chi_hans)

[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)提供了其他 Campaign Classic 操作方法视频。
