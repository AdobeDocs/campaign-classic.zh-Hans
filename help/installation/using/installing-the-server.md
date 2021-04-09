---
solution: Campaign Classic
product: campaign
title: 安装服务器
description: 安装服务器
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: c0cb4efa-cae9-4312-88fb-738857a89595
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 2%

---

# 安装服务器{#installing-the-server}

## 执行安装项目{#executing-the-installation-program}

对于Windows 32位平台，请安装32位Adobe Campaign。 对于Windows 64位平台，请安装64位Adobe Campaign。

Adobe Campaign服务器的安装步骤如下：

1. 执行文件&#x200B;**setup.exe**。

   ![](assets/s_ncs_install_installer_01.png)

1. 选择安装类型。

   ![](assets/s_ncs_install_installer_01a.png)

   有几种安装类型可用：

   * **[!UICONTROL Installation of an application server]** :安装Adobe Campaign应用程序服务器和客户端控制台。
   * **[!UICONTROL Minimal installation (Network)]** :从网络安装客户端计算机。如果需要，计算机上将只安装有限数量的DLL，所有其他组件将从网络驱动器中使用。
   * **[!UICONTROL Installation of a client]** :安装Adobe Campaign客户端所需的组件。
   * **[!UICONTROL Custom installation]** :用户选择要安装的元素。

   选择&#x200B;**安装应用程序服务器**，然后执行以下不同步骤：

   ![](assets/s_ncs_install_installer_02.png)

1. 选择安装目录：

   ![](assets/s_ncs_install_installer_03.png)

1. 单击&#x200B;**[!UICONTROL Finish]**&#x200B;开始安装：

   ![](assets/s_ncs_install_installer_04.png)

   进度栏显示安装的距离：

   ![](assets/s_ncs_install_installer_05.png)

   安装完成后，将显示一条消息，通知您：

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >服务器安装完成后，需要重新启动服务器以避免可能出现的网络问题。

   安装完成后，开始Adobe Campaign创建配置文件。 请参阅服务器](#first-start-up-of-the-server)的第一个开始。[

## 安装测试摘要{#summary-installation-testing}

可以使用以下命令测试初始安装：

```
nlserver pdump
```

如果Adobe Campaign未启动，则响应为：

```
No task
```

## 服务器{#first-start-up-of-the-server}的首次开始

安装测试完成后，通过&#x200B;**[!UICONTROL Start > Programs > Adobe Campaign]**&#x200B;菜单打开命令提示符，然后输入以下命令：

```
nlserver web
```

![](assets/s_ncs_install_cmd_nlserverweb.png)

安装目录中的文件用于配置Adobe Campaign服务器模块。

将显示以下信息：

```
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

按&#x200B;**Ctrl+C**&#x200B;可停止进程，然后输入以下命令：

```
nlserver start web
```

将显示以下信息：

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Start of the 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') task in a new process 
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Generation of configuration changes '[INSTALL]bin..confserverConf.xml.diff' between '[INSTALL]bin..confserverConf.xml' and '[INSTALL]bin..conffraserverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

要停止，请输入：

```
nlserver stop web
```

将显示以下信息：

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## 内部标识符{#password-for-the-internal-identifier}的口令

Adobe Campaign服务器定义名为&#x200B;**internal**&#x200B;的技术登录，该登录对所有实例具有所有权限。 安装后，登录名没有密码。 必须定义一个。

请阅读[本节](../../installation/using/configuring-campaign-server.md#internal-identifier)了解更多信息。

## 正在启动Adobe Campaign服务{#starting-adobe-campaign-services}

要开始Adobe Campaign服务，您可以使用服务管理器或在命令行中输入以下内容（具有相应权限）：

```
net start nlserver6
```

如果您需要稍后停止Adobe Campaign进程，请使用以下命令：

```
net stop nlserver6
```

## 安装LibreOffice {#installing-libreoffice}

例如，从[https://www.libreoffice.org/download/libreoffice-fresh/](https://www.libreoffice.org/download/libreoffice-fresh/)下载LibreOffice，然后按照常规安装步骤操作。

添加以下环境变量：

```
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```
