---
title: 集成到Windows版Web服务器
seo-title: 集成到Windows版Web服务器
description: 集成到Windows版Web服务器
seo-description: null
page-status-flag: never-activated
uuid: a5042221-44fe-46a6-9322-288b108396e2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: a4f2ae0e-e631-4ab6-934e-8298e4ce6f2c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: abddb3cdfcee9e41cab2e7e662d5bfd5d53d6f7e

---


# 集成到Windows版Web服务器{#integration-into-a-web-server-for-windows}

Adobe Campaign包含Apache Tomcat，它通过HTTP（和SOAP）充当应用程序服务器中的入口点。

您可以使用此集成的Tomcat服务器来提供HTTP请求。

在这种情况下：

* 默认监听端口为8080。 要更改它，请参阅配 [置Tomcat](../../installation/using/configuring-campaign-server.md#configuring-tomcat)。
* 然后，客户端控制台使用URL进行连 [接， `<computer>`如https://:8080](https://machine:8080)。

但是，出于安全和管理原因，当运行Adobe Campaign的计算机在Internet上公开并且您希望打开对网络外控制台的访问时，我们建议使用专用Web服务器作为HTTP通信的主要入口点。

Web服务器还允许您使用HTTP协议保证数据的机密性。

同样，当您希望使用跟踪功能时，必须使用Web服务器，该功能仅作为Web服务器扩展模块可用。

>[!NOTE]
>
>如果不使用跟踪功能，则可以通过重定向到Campaign来执行Apache或IIS的标准安装。 无需跟踪Web服务器扩展模块。

## 配置IIS web服务器 {#configuring-the-iis-web-server}

IIS web服务器的配置过程大多是图形化的。 它涉及使用网站（已创建或待创建）访问Adobe Campaign服务器的资源：Java(.jsp)文件、样式表(.css、.xsl)、图像(.png)、重定向的ISAPI DLL等。

IIS 7中的以下部分详细配置。 IIS8的配置基本相同。

如果您的计算机上尚未安装Web IIS服务器，则可以通过菜单安装该服 **[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]** 务器。

在IIS 7中，除了标准服务，您还需要安装ISAPI扩展和ISAPI过滤器。

![](assets/s_ncs_install_iis7_isapi.png)

### 配置步骤 {#configuration-steps}

应用以下配置步骤：

1. 通过菜单打开IIS **[!UICONTROL Control panel > Administrative tools > Services]** 。
1. 根据网络参数（TCP连接端口、DNS主机、IP地址）创建和配置站点（例如Adobe Campaign）。

   ![](assets/s_ncs_install_iis7_add_site.png)

   您必须至少指定站点的名称和虚拟目录的访问路径。 由于未使用访问网站目录的路径，因此可以使用以下目录。

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. VBS **** 脚本允许您在我们刚刚创建的虚拟目录上自动配置Adobe Campaign服务器使用的资源。 要启动它，请双击位于文 **件夹中的iis_neolane_setup.vbs** ，其中 `[INSTALL]\tomcat-7\conf``[INSTALL]` 是访问Adobe Campaign安装文件夹的路径。

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >如果安装了Windows服务器2008/IIS7，则必须以管理员身份登录才能运行VBS脚本或以管理员身份执行脚本。

   如果 **[!UICONTROL OK]** Web服务器用作跟踪重定向服务器，请单击，否则单击 **[!UICONTROL Cancel]**。

   当Web服务器上已配置多个站点时，将显示一个中间页面，以指定安装应用于哪个Web站点：输入链接到该站点的编号，然后单击 **[!UICONTROL OK]**。

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   应显示确认消息：

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. 在选项卡 **[!UICONTROL Content View]** 中，确保网站已正确配置了Adobe Campaign资源：

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   如果未显示树，请重新启动IIS。

### 管理权限 {#managing-rights}

您随后必须为ISAPI DLL和Adobe Campaign安装目录中的资源配置安全设置。

为此，请应用以下步骤：

1. 选择选 **[!UICONTROL Features View]** 项卡，然后双击“身份验 **证** ”链接。

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. 在网站 **的“目录安全** ”选项卡中，确保启用匿名访问。 如有必要，请单 **[!UICONTROL Edit]** 击链接以更改设置。

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### 启动Web服务器并测试配置 {#launching-the-web-server-and-testing-the-configuration}

您现在必须测试配置是否正确。

为此，请应用以下过程：

1. 使用isreset命令行重新启动IIS **服务器** 。
1. 将以下URL插入Web浏览器，测试跟踪模块：

   ```
   https://<computer>/r/test
   ```

   浏览器应显示以下响应：

   ```
   <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='myserver.mydomain.com' localHost='localhost'/>
   ```

要测试重定向模块是否存在，请运行以下命令行：

```
nlserver pdump
```

它必须返回以下信息：

```
12:00:33 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

您还可以确保ISAPI DLL正确加载。

为此，请应用以下步骤：

1. 通过单击图标，编辑Adobe Campaign站点的ISAPI过 **[!UICONTROL Driver mapping]** 滤器。
1. 检查ISAPI过滤器的内容：

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## 其他配置 {#additional-configurations}

### 更改上传文件大小限制 {#changing-the-upload-file-size-limit}

配置IIS web服务器时，上传到服务器的设置文件的限制为28 MB左右。

这可能会在Adobe Campaign中产生影响，尤其是如果您要上传大于此限制的文件。

例如，如果您在工作流中使用数据加载 **** （文件）类型活动来导入50 MB的文件，则会出现一个错误，导致该工作流无法正确执行。

在这种情况下，您必须提高此限制：

1. 通过菜单打开IIS **[!UICONTROL Start > (Control panel) > Administration tools]** 。
1. 在“连 **接** ”窗格中，选择为Adobe安装创建的站点，然后在主窗格中双击“ **请求过滤** ”。
1. 在“操 **作** ”窗格中，选择“编 **辑功能设置** ”以能够编辑“最大授权内容大小（字节）”字段 **中的值** 。

   例如，要授权上传50 MB的文件，必须指定大于“52428800”字节的值。

>[!NOTE]
>
>有关此IIS选项的详细信息，请参阅官方文档的“操作方法” [部分](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)。

### 配置http错误消息显示 {#configuring-http-error-message-display}

如果使用6.1版本的IIS服务器，则由于消息中显示不需要的HTML代码，所生成的错误消息可能难以读取。

要修复此问题并正确显示错误，请应用以下配置：

1. 通过菜单打开IIS **[!UICONTROL Start > Control Panel > Administrative tools]** 。
1. 在“连 **接** ”窗格中，选择为Adobe Campaign安装创建的站点，然后在主窗格中双击“ **配置编辑器** ”。
1. 在“ **节** ”下拉列表中，选择 **system.webServer** > **httpErrors**。
1. 在现有 **Response行上** ，选择 **PassThrough值** 。

![](assets/ins_iis_httperrors.png)

