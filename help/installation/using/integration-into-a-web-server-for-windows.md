---
product: campaign
title: 集成到 Windows 版 Web 服务器
description: 集成到 Windows 版 Web 服务器
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 041c4431-baae-4e64-9e9a-0daa5123bd8a
source-git-commit: 3958fff140cc9bf6c371f0c4207cafc9a27bb725
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 2%

---

# 集成到 Windows 版 Web 服务器{#integration-into-a-web-server-for-windows}

Adobe Campaign包含Apache Tomcat，它通过HTTP（和SOAP）作为应用程序服务器中的入口点。

您可以使用此集成的Tomcat服务器来提供HTTP请求。

在这种情况下：

* 默认监听端口为8080。 要更改，请参阅[此部分](../../installation/using/configure-tomcat.md)。
* 然后，客户端控制台使用URL(如[https:// `<computer>`:8080](https://myserver.adobe.com:8080))进行连接。

但是，出于安全和管理原因，当运行Adobe Campaign的计算机在Internet上公开并且您希望打开对网络外部控制台的访问时，我们建议使用专用Web服务器作为HTTP流量的主入口点。

Web服务器还允许您使用HTTPs协议保证数据的机密性。

同样，当您希望使用跟踪功能时，必须使用Web服务器，该功能仅作为Web服务器扩展模块提供。

>[!NOTE]
>
>如果不使用跟踪功能，则可以通过重定向到Campaign来执行Apache或IIS的标准安装。 不需要跟踪Web服务器扩展模块。

## 配置IIS Web服务器 {#configuring-the-iis-web-server}

IIS Web服务器的配置过程主要是图形化的。 它涉及使用网站（已创建或待创建）访问Adobe Campaign服务器的资源：Java(.jsp)文件、样式表(.css、.xsl)、图像(.png)、用于重定向的ISAPI DLL等。

以下各节详细介绍了IIS 7中的配置。 IIS8的配置基本相同。

如果您的计算机上尚未安装Web IIS服务器，则可以通过&#x200B;**[!UICONTROL Add > Remove Programs > Enable or disable Windows functionalities]**&#x200B;菜单进行安装。

在IIS 7中，除了标准服务之外，您还需要安装ISAPI扩展和ISAPI过滤器。

![](assets/s_ncs_install_iis7_isapi.png)

### 配置步骤 {#configuration-steps}

应用以下配置步骤：

1. 通过&#x200B;**[!UICONTROL Control panel > Administrative tools > Services]**&#x200B;菜单打开IIS。
1. 根据网络参数（TCP连接端口、DNS主机、IP地址）创建和配置站点(例如Adobe Campaign)。

   ![](assets/s_ncs_install_iis7_add_site.png)

   必须至少指定站点名称和虚拟目录的访问路径。 由于未使用访问Website目录的路径，因此可以使用以下目录。

   ```
   C:\inetpub\wwwroot
   ```

   ![](assets/s_ncs_install_iis7_parameters_step1.png)

1. 使用&#x200B;**VBS**&#x200B;脚本，可以自动配置Adobe Campaign服务器在我们刚刚创建的虚拟目录上使用的资源。 要启动该文件，请双击位于`[INSTALL]\conf`文件夹中的&#x200B;**iis_neolane_setup.vbs**&#x200B;文件，其中`[INSTALL]`是访问Adobe Campaign安装文件夹的路径。

   ![](assets/s_ncs_install_iis7_parameters_step2.png)

   >[!NOTE]
   >
   >如果安装了Windows服务器2008/IIS7，则必须以管理员身份登录才能运行VBS脚本或以管理员身份执行脚本。

   如果Web服务器用作跟踪重定向服务器，请单击&#x200B;**[!UICONTROL OK]**，否则单击&#x200B;**[!UICONTROL Cancel]**。

   在Web服务器上已配置多个网站时，将显示一个中间页面，以指定安装所应用的网站：输入链接到站点的编号，然后单击&#x200B;**[!UICONTROL OK]**。

   ![](assets/s_ncs_install_iis7_parameters_step3.png)

   应显示确认消息：

   ![](assets/s_ncs_install_iis7_parameters_step7.png)

1. 在&#x200B;**[!UICONTROL Content View]**&#x200B;选项卡中，确保使用Adobe Campaign资源正确配置了网站：

   ![](assets/s_ncs_install_iis7_parameters_step6.png)

   如果未显示树，请重新启动IIS。

### 管理权限 {#managing-rights}

接下来，必须在Adobe Campaign安装目录中为ISAPI DLL和资源配置安全设置。

要执行此操作，请应用以下步骤：

1. 选择&#x200B;**[!UICONTROL Features View]**&#x200B;选项卡，然后双击&#x200B;**Authentication**&#x200B;链接。

   ![](assets/s_ncs_install_iis7_parameters_step8.png)

1. 在网站的&#x200B;**Directory Security**&#x200B;选项卡中，确保启用匿名访问。 如有必要，单击&#x200B;**[!UICONTROL Edit]**&#x200B;链接以更改设置。

   ![](assets/s_ncs_install_iis7_parameters_step9.png)

### 启动Web服务器并测试配置 {#launching-the-web-server-and-testing-the-configuration}

您现在必须测试配置是否正确。

要执行此操作，请应用以下过程：

1. 使用&#x200B;**iisreset**&#x200B;命令行重新启动IIS服务器。

1. 启动Adobe Campaign服务，然后确保该服务正在运行。

1. 通过将以下URL插入Web浏览器来测试跟踪模块：

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

必须返回以下信息：

```
12:00:33 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
webmdl@default (1644) - 18.2 Mo
```

您还可以确保ISAPI DLL正确加载。

要执行此操作，请应用以下步骤：

1. 通过单击&#x200B;**[!UICONTROL Driver mapping]**&#x200B;图标，编辑Adobe Campaign站点的ISAPI过滤器。
1. 检查ISAPI过滤器的内容：

   ![](assets/s_ncs_install_iis7_parameters_step11.png)

## 其他配置 {#additional-configurations}

### 更改上传文件大小限制 {#changing-the-upload-file-size-limit}

在配置IIS Web服务器时，对于上传到服务器的设置文件，自动限制大约为28 MB。

这可能会在Adobe Campaign中产生影响，特别是如果您要上载大于此限制的文件。

例如，如果您在工作流中使用&#x200B;**数据加载（文件）**&#x200B;类型活动来导入50 MB的文件，则错误会阻止工作流正确执行。

在这种情况下，您必须提高此限制：

1. 通过&#x200B;**[!UICONTROL Start > (Control panel) > Administration tools]**&#x200B;菜单打开IIS。
1. 在&#x200B;**连接**&#x200B;窗格中，选择为Adobe安装创建的站点，然后双击主窗格中的&#x200B;**请求筛选**。
1. 在&#x200B;**操作**&#x200B;窗格中，选择&#x200B;**编辑功能设置**&#x200B;以能够编辑&#x200B;**最大授权内容大小（字节）**&#x200B;字段中的值。

   例如，要授权上载50 MB的文件，您必须指定一个大于“52428800”字节的值。

>[!NOTE]
>
>有关此IIS选项的更多信息，请参阅[官方文档](https://www.iis.net/configreference/system.webserver/security/requestfiltering/requestlimits)的“操作方法”部分。

### 配置http错误消息显示 {#configuring-http-error-message-display}

如果您使用6.1版本的IIS服务器，则可能由于消息中显示了不需要的HTML代码而难以读取生成的错误消息。

要修复此问题并正确显示错误，请应用以下配置：

1. 通过&#x200B;**[!UICONTROL Start > Control Panel > Administrative tools]**&#x200B;菜单打开IIS。
1. 在&#x200B;**连接**&#x200B;窗格中，选择为Adobe Campaign安装创建的站点，然后双击主窗格中的&#x200B;**配置编辑器**。
1. 在&#x200B;**Section**&#x200B;下拉列表中，选择&#x200B;**system.webServer** > **httpErrors**。
1. 在&#x200B;**existingResponse**&#x200B;行中选择&#x200B;**PassThrough**&#x200B;值。

![](assets/ins_iis_httperrors.png)
