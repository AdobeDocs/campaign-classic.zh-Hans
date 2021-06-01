---
product: campaign
title: 升级到新内部版本
description: 了解升级到新内部版本的技术步骤
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1149'
ht-degree: 2%

---

# 升级到新内部版本（内部部署）{#upgrading}

在开始升级过程之前，请确定并确认要升级到的Adobe Campaign版本，并查阅[发行说明](../../rn/using/latest-release.md) 。

>[!IMPORTANT]
>
>* Adobe强烈建议在更新之前对每个实例进行数据库备份。 有关更多信息，请参见[此章节](../../production/using/backup.md)。
>* 要执行升级，请确保您具有访问实例和日志的功能和权限。
>* 在开始之前，请阅读[此部分](../../installation/using/general-architecture.md)和[内部版本升级](https://helpx.adobe.com/cn/campaign/kb/acc-build-upgrade.html)章节。

>



## Windows {#in-windows}

在Windows环境中，按照以下步骤将Adobe Campaign更新为新内部版本：

* [关闭服务](#shut-down-services),
* [升级应用程序服务器](#upgrade-the-adobe-campaign-server-application),
* [同步资源](#synchronize-resources)、
* [重新启动服务](#restart-services)。

要了解如何更新客户端控制台，请参阅[此部分](../../installation/using/client-console-availability-for-windows.md)。

### 关闭服务{#shut-down-services}

若要使用新版本替换所有文件，您需要关闭nlserver服务的所有实例。

1. 关闭以下服务：

   * Web服务(IIS):

      **iisreset /stop**

   * Adobe Campaign服务：**net stop nlserver6**
   >[!IMPORTANT]
   >
   >您还需要确保已停止重定向服务器(webmdl)，以便IIS使用的&#x200B;**nlsrvmod.dll**&#x200B;文件可以替换为新版本。

1. 运行&#x200B;**nlserver pdump**&#x200B;命令，检查没有任务处于活动状态。 应当出现以下内容：

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   您可以使用Windows任务管理器来确保所有进程都已停止。

### 升级Adobe Campaign服务器应用程序{#upgrade-the-adobe-campaign-server-application}

要运行升级文件，请应用以下步骤：

1. 运行&#x200B;**setup.exe**。

   要下载此文件，请使用您的用户凭据连接到[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。 详细了解[本页](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)中的软件分发。

1. 选择安装模式：选择&#x200B;**[!UICONTROL Update or repair]**
1. 单击 **[!UICONTROL Next]**。
1. 单击 **[!UICONTROL Finish]**。

   然后，安装程序复制新文件。

1. 操作完成后，单击&#x200B;**[!UICONTROL Finish]** 。

### 同步资源{#synchronize-resources}

使用以下命令行：

**nlserver config -postupgrade -allinstances**

这样，您就可以执行以下操作：

* 同步资源
* 更新架构
* 更新数据库

>[!NOTE]
>
>此操作只应在(**nlserver web**)应用程序服务器上执行一次。

然后，检查同步是否生成了错误或警告。 有关更多信息，请参阅[解决升级冲突](#resolving-upgrade-conflicts)。

### 重新启动服务{#restart-services}

要重新启动的服务包括：

* Web服务(IIS):

   **iisreset /start**

* Adobe Campaign服务：**net start nlserver6**

## Linux {#in-linux}

在Linux环境中，按照以下步骤将Adobe Campaign更新为新内部版本：

* [下载更新的包](#obtain-updated-packages)、
* [执行更新](#perform-an-update),
* [重新启动Web服务器](#reboot-the-web-server)。

[了解有关客户端控制台可用性的更多信息](../../installation/using/client-console-availability-for-windows.md)。

>[!NOTE]
>
>从版本8757开始，不再需要第三方库。

### 获取更新的包{#obtain-updated-packages}

首先，恢复两个更新的Adobe Campaign包：使用您的用户凭据连接到[Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)。 详细了解[本页](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)中的软件分发。

文件为&#x200B;**nlserver6-v7-XXX.rpm**

### 执行更新{#perform-an-update}

* 基于RPM的分发(RedHat、SuSe)

   要安装它们，请以root身份执行：

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   其中XXX是文件的版本。

   rpm文件依赖于CentOS/Red Hat分发包。 如果您不想使用某些依赖项，则可能必须使用rpm的“nodeps”选项：

   ```
   rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
   ```

* 基于DEB的分发(Debian)

   要安装它们，请以root身份执行：

   ```
   dpkg -i nlserver6-v7-XXXX-amd64_debX.deb
   ```

>[!NOTE]
>
>[此部分](../../installation/using/installing-campaign-standard-packages.md)中详细描述了完整的安装过程。 资源会自动同步，但您需要确保未发生错误。 有关更多信息，请参阅[解决升级冲突](#resolving-upgrade-conflicts)。

### 重新启动Web服务器{#reboot-the-web-server}

必须关闭Apache才能使新库适用。

为此，请执行以下命令：

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* 您的脚本可能名为&#x200B;**httpd**，而不是&#x200B;**apache**。
>* 必须执行此命令，直到您获得以下答复：

   >
   >   
   要使Apache应用新库，需要执行此操作。


然后重新启动Apache:

```
/etc/init.d/apache start
```

## 解决升级冲突{#resolving-upgrade-conflicts}

在资源同步期间，使用&#x200B;**postupgrade**&#x200B;命令可以检测同步是否生成了错误或警告。

### 查看同步结果{#view-the-synchronization-result}

有两种查看同步结果的方法：

* 在命令行界面中，错误由三个V形标记&#x200B;**>>**&#x200B;实现，并自动停止同步。 警告由双V形标记&#x200B;**>>**&#x200B;实现，并且必须在同步完成后进行解析。 在升级后，命令提示符中会显示一个摘要。 它可以如下所示：

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   如果警告涉及资源冲突，则需要用户注意才能解决该问题。

* **postupgrade_`<server version number>_<time of postupgrade>`.log**&#x200B;日志文件包含同步结果。 默认情况下，该插件可在以下目录中使用：**`<installation directory>/var/<instance/postupgrade`**。 错误和警告属性会指示错误和警告。

### 解决冲突{#resolving-conflicts}

要解决冲突，请应用以下流程：

1. 在Adobe Campaign树中，转到&#x200B;**[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** 。
1. 在列表中选择要解决的冲突。

解决冲突有三种方法：

* **[!UICONTROL Declare as resolved]** :需要事先进行用户干预。
* **[!UICONTROL Accept the new version]** :如果用户未更改随Adobe Campaign提供的资源，则建议使用此选项。
* **[!UICONTROL Keep the current version]** :表示更新被拒绝。

   >[!IMPORTANT]
   >
   >如果选择此分辨率模式，则新版本中的更正可能不会对您有所帮助。

如果您选择手动解决冲突，请按如下方式继续：

1. 在窗口的下部，搜索&#x200B;**_conflict_**&#x200B;字符串以查找存在冲突的实体。 随新版本一起安装的实体包含&#x200B;**new**&#x200B;参数，与先前版本匹配的实体包含&#x200B;**cus**&#x200B;参数。

   ![](assets/s_ncs_production_conflict002.png)

1. 删除您不希望保留的版本。 删除要保留的实体的&#x200B;**_conflict_argument_**&#x200B;字符串。

   ![](assets/s_ncs_production_conflict003.png)

1. 转到已解决的冲突。 单击&#x200B;**[!UICONTROL Actions]**&#x200B;图标，然后选择&#x200B;**[!UICONTROL Declare as resolved]** 。
1. 保存更改：冲突现已解决。

### 最佳做法 {#best-practices}

更新失败可能已链接到数据库配置。 确保技术管理员和数据库管理员执行的配置兼容。

例如，Unicode数据库不仅必须授权存储LATIN1数据等。

## 警告客户端控制台可用更新{#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

在安装Adobe Campaign应用程序服务器的计算机上(**nlserver web**)，下载并复制文件&#x200B;**setup-client-6.XXXX.exe** ，它位于&#x200B;**[应用程序的路径]/datakit/nl/eng/jsp**&#x200B;中。

下次连接客户端控制台时，窗口会告知用户更新的可用性，并为用户提供下载和安装更新的可能性。

>[!NOTE]
>
>请确保IIS_XPG用户具有此安装文件的适当读取权限，并参阅[安装指南](../../installation/using/general-architecture.md)以了解详细信息。

### Linux {#in-linux-1}

在安装Adobe Campaign应用程序服务器(**nlserver web**)的计算机上，检索&#x200B;**setup-client-6.XXXX.exe**&#x200B;包并复制它，另存为&#x200B;**/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

下次连接客户端控制台时，窗口会告知用户更新的可用性，并为用户提供下载和安装更新的可能性。

>[!NOTE]
>
>请确保Apache用户具有此安装文件的相应读取权限，并参阅[安装指南](../../installation/using/general-architecture.md)以了解详细信息。
