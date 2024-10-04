---
product: campaign
title: 升级到新内部版本
description: 了解升级到新内部版本的技术步骤
feature: Monitoring, Upgrade
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4aaa6256-256a-441d-80c9-430f8e427875
source-git-commit: 0da7fb912a909af222d796652efba4b30e39dc1c
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 2%

---

# 升级到新内部版本（内部部署）{#upgrading}

在开始升级过程之前，请确定并确认要升级到哪个Adobe Campaign版本，并参阅[发行说明](../../rn/using/latest-release.md) 。

>[!IMPORTANT]
>
>* Adobe强烈建议在更新之前对每个实例进行数据库备份。 有关更多信息，请参见[此章节](../../production/using/backup.md)。
>* 要执行升级，请确保您有权访问实例和日志。
>* 在开始之前，请先阅读[此部分](../../installation/using/general-architecture.md)和[内部版本升级](https://helpx.adobe.com/cn/campaign/kb/acc-build-upgrade.html)章节。
>

## Windows {#in-windows}

在Windows环境中，执行以下步骤以将Adobe Campaign更新到新内部版本：

* [关闭服务](#shut-down-services)，
* [升级应用程序服务器](#upgrade-the-adobe-campaign-server-application)，
* [同步资源](#synchronize-resources)，
* [重新启动服务](#restart-services)。

要了解如何更新客户端控制台，请参阅[此部分](../../installation/using/client-console-availability-for-windows.md)。

### 关闭服务 {#shut-down-services}

要使用新版本替换所有文件，您需要关闭nlserver服务的所有实例。

1. 关闭以下服务：

   * Web服务(IIS)：

     **iisreset /stop**

   * Adobe Campaign服务：**net stop nlserver6**

   >[!IMPORTANT]
   >
   >您还需要确保重定向服务器(webmdl)已停止，以便能够将IIS使用的&#x200B;**nlsrvmod.dll**&#x200B;文件替换为新版本。

1. 通过运行&#x200B;**nlserver pdump**&#x200B;命令检查没有活动的任务。 应出现以下内容：

   ```sql
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   您可以使用Windows任务管理器确保所有进程都已停止。

### 升级Adobe Campaign服务器应用程序 {#upgrade-the-adobe-campaign-server-application}

要运行升级文件，请应用以下步骤：

1. 运行&#x200B;**setup.exe**。

   若要下载此文件，请使用用户凭据连接到[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html)。 在[此页面](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hans)中了解有关软件分发的更多信息。

1. 选择安装模式：选择&#x200B;**[!UICONTROL Update or repair]**
1. 单击&#x200B;**[!UICONTROL Next]** 。
1. 单击&#x200B;**[!UICONTROL Finish]** 。

   然后，安装程序将复制新文件。

1. 操作完成后，单击&#x200B;**[!UICONTROL Finish]** 。

### 同步资源 {#synchronize-resources}

使用以下命令行：

**nlserver配置 — postupgrade -allinstances**

这样，您就可以执行以下操作：

* 同步资源
* 更新架构
* 更新数据库

>[!NOTE]
>
>此操作只应在(**nlserver web**)应用程序服务器上执行一次。

然后检查同步是否生成了错误或警告。 有关详细信息，请参阅[解决升级冲突](#resolving-upgrade-conflicts)。

### 重新启动服务 {#restart-services}

要重新启动的服务包括：

* Web服务(IIS)：

  **iisreset /start**

* Adobe Campaign服务：**net start nlserver6**

## Linux {#in-linux}

在Linux环境中，执行以下步骤以将Adobe Campaign更新到新内部版本：

* [下载更新的包](#obtain-updated-packages)，
* [执行更新](#perform-an-update)，
* [重新启动Web服务器](#reboot-the-web-server)。

[了解有关客户端控制台可用性的详细信息](../../installation/using/client-console-availability-for-windows.md)。

### 安装更新的包 {#obtain-updated-packages}

首先恢复Adobe Campaign的两个更新包：使用您的用户凭据连接到[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/cn/campaign.html)。 在[此页面](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hans)中了解有关软件分发的更多信息。

文件为&#x200B;**nlserver6-v7-XXX.rpm**

>[!AVAILABILITY]
>
>从 v7.4.1 开始，Campaign 中不再包含 RPM Linux 包的 XML 库。您必须安装这些库。
> 

然后，您可以安装所需的包，如下所述：

* 基于RPM的分发(RedHat、SuSe)

  如果未安装`epel-release`包，请安装它。 要执行此操作，请以root身份输入以下命令：

  ```
  yum install epel-release
  ```

  要安装Campaign包，请以根用户身份执行：

  ```
  yum update ./nlserver6-v7-XXXX.rpm
  ```

  在确认更新之前，请确保输出如下所示：

  ```
  ==================================================================================================== 
  Package                         Architecture  Version                    Repository           Size 
  ==================================================================================================== 
  Upgrading: 
  nlserver6-v7                    x86_64        XXXX.0.0-1                 @commandline         63 M
  ```

  >[!IMPORTANT]
  >
  >如果您读取的是`Removing:`而不是`Upgrading:`，请取消该命令。 可能有一些错误（如上面所列）解释了删除操作。 在这种情况下，请通过更新/安装列出的缺失依赖项来更正这些错误，然后再次尝试运行该命令。

  rpm文件依赖于可在CentOS/Red Hat分发中找到的软件包。 如果不想使用某些依赖关系，则可能需要使用rpm的“nodeps”选项：

  ```
  rpm --nodeps -Uvh nlserver6-v7-XXXX-0.x86_64.rpm
  ```

  请注意，大多数依赖项是必需的，如果没有安装，`nlserver`将无法启动。 唯一的例外是openjdk，如果需要，您可以安装另一个JDK。

* 基于DEB的分发(Debian)

  要安装它们，请以root身份执行：

  ```
  apt install ./nlserver6-v7-XXXX-amd64_debX.deb
  ```

>[!NOTE]
>
>[本节](../../installation/using/installing-packages-with-linux.md)中详细介绍了完整安装程序。 资源会自动同步，但您需要确保没有发生错误。 有关详细信息，请参阅[解决升级冲突](#resolving-upgrade-conflicts)。
>

### 重新启动Web服务器 {#reboot-the-web-server}

您必须关闭Apache才能使新库适用。

为此，请执行以下命令：

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* 您的脚本可能名为&#x200B;**httpd**，而不是&#x200B;**apache**。
>* 必须执行此命令，直到获得以下回复为止：
>
>   `This operation is required in order for Apache to apply the new library.`

然后重新启动Apache：

```
/etc/init.d/apache start
```

## 解决升级冲突 {#resolving-upgrade-conflicts}

在资源同步过程中，**升级后**&#x200B;命令允许您检测同步是否生成了错误或警告。

### 查看同步结果 {#view-the-synchronization-result}

查看同步结果的方法有两种：

* 在命令行界面中，错误由三个V形&#x200B;**>>**&#x200B;实现，同步自动停止。 警告以双V形&#x200B;**>>**&#x200B;实现，同步完成后必须解决这些警告。 升级后结束时，命令提示符中会显示摘要。 它看上去可能如下所示：

  ```
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  AAAA-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  如果警告与资源冲突有关，则需要用户注意才能解决该问题。

* **postupgrade_`<server version number>_<time of postupgrade>`.log**&#x200B;日志文件包含同步结果。 默认情况下，它在以下目录中可用： **`<installation directory>/var/<instance/postupgrade`**。 错误和警告属性表示错误和警告。

### 解决冲突 {#resolving-conflicts}

要解决冲突，请应用以下流程：

1. 在Adobe Campaign树中，转到&#x200B;**[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** 。
1. 在列表中选择要解决的冲突。

解决冲突的方法有三种：

* **[!UICONTROL Declare as resolved]** ：需要用户提前干预。
* **[!UICONTROL Accept the new version]** ：如果用户未更改随Adobe Campaign提供的资源，则建议这样做。
* **[!UICONTROL Keep the current version]** ：表示更新被拒绝。

  >[!IMPORTANT]
  >
  >如果选择此解决模式，您可能无法受益于新版本中的更正。

如果您选择手动解决冲突，请按以下步骤操作：

1. 在窗口的下部，搜索&#x200B;**_冲突_**&#x200B;字符串以查找存在冲突的实体。 与新版本一起安装的实体包含&#x200B;**new**&#x200B;参数，与先前版本匹配的实体包含&#x200B;**cus**&#x200B;参数。

   ![](assets/s_ncs_production_conflict002.png)

1. 删除您不想保留的版本。 删除要保留的实体的&#x200B;**_conflict_argument_**&#x200B;字符串。

   ![](assets/s_ncs_production_conflict003.png)

1. 转到您已解决的冲突。 单击&#x200B;**[!UICONTROL Actions]**&#x200B;图标并选择&#x200B;**[!UICONTROL Declare as resolved]** 。
1. 保存更改：冲突现已解决。

### 最佳实践 {#best-practices}

更新失败可能会链接到数据库配置。 确保技术管理员和数据库管理员执行的配置兼容。

例如，Unicode数据库不仅必须授权存储LATIN1数据等，

## 警告客户端控制台有可用的更新 {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

在安装Adobe Campaign应用程序服务器的计算机(**nlserver web**)上，下载并复制文件&#x200B;**setup-client-6.XXXX.exe**，该文件位于应用程序的&#x200B;**[路径中]/datakit/nl/eng/jsp**。

下次连接客户端控制台时，将显示一个窗口，通知用户是否有更新，并允许用户下载和安装更新。

>[!NOTE]
>
>确保IIS_XPG用户对此安装文件具有适当的读取权限，并参阅[安装指南](../../installation/using/general-architecture.md)以了解更多信息。

### Linux {#in-linux-1}

在安装了Adobe Campaign应用程序服务器(**nlserver web**)的计算机上，检索&#x200B;**setup-client-6.XXXX.exe**&#x200B;包并复制它，另存为&#x200B;**/usr/local/neolane/nl6/datakit/nl/eng/jsp**：

```
cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

下次连接客户端控制台时，将显示一个窗口，通知用户是否有更新，并允许用户下载和安装更新。

>[!NOTE]
>
>确保Apache用户对此安装文件具有适当的读取权限，并参阅[安装指南](../../installation/using/general-architecture.md)以了解更多信息。
