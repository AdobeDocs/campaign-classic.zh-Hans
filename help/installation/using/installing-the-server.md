---
product: campaign
title: 安装服务器
description: 安装服务器
feature: Installation, Instance Settings
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: c0cb4efa-cae9-4312-88fb-738857a89595
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 1%

---

# 安装服务器{#installing-the-server}

## 正在执行安装程序 {#executing-the-installation-program}

对于Windows 32位平台，请安装Adobe Campaign 32位。 对于Windows 64位平台，请安装Adobe Campaign 64位。

Adobe Campaign服务器的安装步骤如下：

1. 执行文件 **setup.exe**.

   ![](assets/s_ncs_install_installer_01.png)

1. 选择安装类型。

   ![](assets/s_ncs_install_installer_01a.png)

   提供了几种安装类型：

   * **[!UICONTROL Installation of an application server]** ：安装Adobe Campaign应用程序服务器和客户端控制台。
   * **[!UICONTROL Minimal installation (Network)]** ：从网络安装客户端计算机。 如有必要，计算机上只会安装有限数量的DLL，而所有其他组件都将从网络驱动器中使用。
   * **[!UICONTROL Installation of a client]** ：安装Adobe Campaign客户端所需的组件。
   * **[!UICONTROL Custom installation]** ：用户选择要安装的元素。

   选择 **应用程序服务器的安装**，并完成如下所示的不同步骤：

   ![](assets/s_ncs_install_installer_02.png)

1. 选择安装目录：

   ![](assets/s_ncs_install_installer_03.png)

1. 单击 **[!UICONTROL Finish]** 要开始安装，请执行以下操作：

   ![](assets/s_ncs_install_installer_04.png)

   进度条显示安装的深度：

   ![](assets/s_ncs_install_installer_05.png)

   安装完成后，将显示一条消息，通知您：

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >服务器安装完成后，需要重新启动服务器以避免可能出现的网络问题。

   安装完成后，启动Adobe Campaign以创建配置文件。 请参阅 [服务器的首次启动](#first-start-up-of-the-server).

## 摘要安装测试 {#summary-installation-testing}

可以使用以下命令测试初始安装：

```sql
nlserver pdump
```

如果Adobe Campaign未启动，则响应为：

```sql
No task
```

## 服务器的首次启动 {#first-start-up-of-the-server}

安装测试完成后，打开命令提示符，通过 **[!UICONTROL Start > Programs > Adobe Campaign]** 菜单并输入以下命令：

```sql
nlserver web
```

安装目录中的文件用于配置Adobe Campaign服务器模块。

将显示以下信息：

```sql
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

按 **Ctrl+C** 要停止该进程，请输入以下命令：

```sql
nlserver start web
```

将显示以下信息：

```sql
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Start of the 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') task in a new process 
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Generation of configuration changes '[INSTALL]bin..confserverConf.xml.diff' between '[INSTALL]bin..confserverConf.xml' and '[INSTALL]bin..conffraserverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

要停止此操作，请输入：

```sql
nlserver stop web
```

将显示以下信息：

```sql
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## 内部标识符的密码 {#password-for-the-internal-identifier}

Adobe Campaign服务器定义的技术登录名为 **内部** 拥有所有实例的所有权限。 安装之后，登录没有密码。 必须定义一个。

可在[此部分](../../installation/using/configuring-campaign-server.md#internal-identifier)中了解详情。

## 启动Adobe Campaign服务 {#starting-adobe-campaign-services}

要启动Adobe Campaign服务，您可以使用服务管理器或在命令行中输入以下内容（具有相应权限）：

```sql
net start nlserver6
```

如果您稍后需要停止Adobe Campaign进程，请使用命令：

```sql
net stop nlserver6
```

## 安装LibreOffice {#installing-libreoffice}

下载LibreOffice并遵循常规安装步骤。

添加以下环境变量：

```sql
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```
