---
solution: Campaign Classic
product: campaign
title: 安装客户端控制台
description: 了解如何安装客户端控制台
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: c96a7faf5c65848a3f383a5721bfa45048ecea57
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 5%

---


# 安装和更新活动客户端控制台{#installing-the-client-console}


活动 Client Console是一个富客户端，通过它可以连接到您的活动应用程序服务器。

在启动之前，您需要检查活动[兼容性矩阵](https://helpx.adobe.com/cn/campaign/kb/compatibility-matrix.html)，获取活动服务器URL和用户凭据。

>[!CAUTION]
>
>活动 Client控制台和活动应用程序服务器必须在同一产品版本上运行。 Adobe还建议使用相同的产品版本。

![](assets/do-not-localize/how-to-video.png) 了解如何在视频中安装和设置Adobe Campaign客 [户端](#video)

安装或更新客户端控制台的过程会因您对Adobe Campaign Classic的实施而异。
请查看以下详细信息，了解实施所需的内容。


## Adobe托管实现{#hosted-customers}

要安装或更新您的客户端控制台，请执行以下操作：

1. Adobe可以直接部署。 更新控制台后，将在弹出窗口中提示用户下载最新的客户端控制台版本。

1. 您可以从[软件分发](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)下载到客户端控制台

   **用户需要管理员访问权限才能完成更新。如果用户没有管理员权限，则系统管理员需要部署到所有客户端控制台**



## 混合和完全内部部署实现{#hybrid-onprem-customers}

为了使Adobe Campaign用户能够登录您创建和配置的实例，他们需要使用客户端控制台。

### 使控制台对用户{#make-console-available}可用

当用于开始Adobe Campaign应用程序服务器(nlserver web)的计算机从客户端控制台接收用户连接时，您可以将其配置为通过HTML界面使Adobe Campaign富客户端的设置项目可用。 只要有新版本的客户端控制台可用，用户就会在启动其客户端控制台时被邀请下载它。

为此，您必须：

1. 选择包含控制台安装项目的包。

   对于v7，此文件称为setup-client-7.X.XXXX.exe；对于v6.1，此文件称为setup-client-6.X.XXXX.exe，其中X是Adobe Campaign的子版本，XXXX是内部版本   数字。

1. 将此包复制并粘贴到/datakit/nl/eng/jsp下的Adobe Campaign安装文件夹（在混合安装的营销服务器上）中。

1. 开始Adobe Campaign服务器。

>[!CAUTION]
>
>  Adobe建议取消选择选项&#x200B;**[!UICONTROL No longer ask this question]**，以确保当新版本的控制台可用时，所有用户都会收到警告。  如果选择此选项，则用户将不会收到有关新可用版本的通知。

如果已选择&#x200B;**[!UICONTROL No longer ask this question]**，则可重置此提示。 只有能够编辑Windows注册表的系统管理员才应进行以下更改：

1. 使用&#x200B;**[!UICONTROL Start > Run]**&#x200B;菜单中的&#x200B;**regedit**&#x200B;命令打开注册表编辑器。

1. 搜索节点并展开它。

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. 删除&#x200B;**confAdwerdedUpgrade**&#x200B;条目并关闭注册表编辑器。

>[!NOTE]
>
>如果您将更新的控制台应用于现有实施，用户将自动收到更新其客户端控制台的提示。 如果您是第一次实施活动，则用户需要下载控制台。 有关这两个选项的详细信息，请参见下文

### 更新控制台 — 现有实施{#update-the-client-console}

控制台在活动服务器文件夹中可用后，将在弹出窗口中提示用户下载最新的客户端控制台版本。

**用户需要管理员访问权限才能完成更新。如果用户没有管理员权限，则系统管理员需要部署到所有客户端控制台**


### 下载控制台 — new implementation{#download-the-client-console}

用户现在应按照以下步骤下载并安装控制台：

1. 打开Web浏览器，然后从以下地址下载控制台：

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. 在标识窗口中，输入您的登录名和密码。

   ![](assets/s_ncs_install_setup_download01.png)

   如有必要，请使用在创建实例过程中定义的内部帐户的凭据。

1. 单击安装页上的&#x200B;**[!UICONTROL Download]**&#x200B;链接。
1. 下载并保存客户端安装文件。
1. 在Windows的计算机上执行下载的文件：安装开始。 根据您的Adobe Campaign版本，客户端控制台的默认安装路径为&#x200B;**$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX客户端**，其中“X”为“6”或“7”。

### 创建连接 — 首次仅用户{#create-the-connection}

安装客户端控制台后，请按照以下步骤创建与应用程序服务器的连接：

1. 从&#x200B;**Adobe Campaign**&#x200B;项目组的Windows **[!UICONTROL Start]**&#x200B;菜单开始控制台。

1. 单击凭据字段右上角的链接以访问连接配置窗口。

   ![](assets/s_ncs_install_define_connection_01.png)

1. 单击&#x200B;**[!UICONTROL Add > Connection]**&#x200B;并输入Adobe Campaign应用程序服务器的标签和URL。

   ![](assets/s_ncs_install_define_connection_02.png)

1. 指定通过URL与Adobe Campaign应用程序服务器的连接。 使用DNS或计算机的别名，或您的IP地址。

   例如，可以使用[`https://<machine>.<domain>.com`](https://myserver.adobe.com)类型URL。

1. 如果为您的组织配置了Adobe IMS，请选中选项&#x200B;**[!UICONTROL Connect with an Adobe ID]**

1. 单击&#x200B;**[!UICONTROL Ok]**&#x200B;保存设置。

例如，您可以根据需要添加任意数量的连接以连接到测试、舞台和生产环境。

>[!NOTE]
>
>通过&#x200B;**[!UICONTROL Add]**&#x200B;按钮可创建&#x200B;**[!UICONTROL folders]**&#x200B;来组织所有连接。 只需将每个连接拖放到某个文件夹中。

### 登录到Adobe Campaign

要登录到现有实例，请执行以下步骤：

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

其他Campaign Classic操作视频[此处](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hans)可用。
