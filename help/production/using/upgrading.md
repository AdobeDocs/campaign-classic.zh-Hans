---
title: 升级到新版本
description: 了解升级到新版本的技术步骤
page-status-flag: never-activated
uuid: f24552d4-6bdf-411c-a1f2-b8f339c311f4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: f8e3633d-7232-44a5-842b-1a70c4f2bca2
translation-type: tm+mt
source-git-commit: 7e56e4f98ffab752f0b86bb8620fb1b4af6a3dca
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 1%

---


# 升级到新版本（内部部署）{#upgrading}

在开始升级过程之前，确定并确认要升级到哪个版本的Adobe Campaign，并参阅 [发行说明](../../rn/using/latest-release.md) 。

>[!IMPORTANT]
>
>我们强烈建议在更新之前对每个实例进行数据库备份。 有关详细信息，请参阅 [备份](../../production/using/backup.md)。\
>要执行升级，请确保您具有访问实例和日志的能力和权限。

>[!NOTE]
>
>另请参阅安装 [指南](../../installation/using/general-architecture.md) 和内 [部升级](https://helpx.adobe.com/cn/campaign/kb/acc-build-upgrade.html) 入门。

## Windows {#in-windows}

要在传送新版本时更新新版本中的Adobe Campaign，应在Windows中应用以下过程：

* [关闭服务](#shut-down-services),
* [升级Adobe Campaign服务器应用程序](#upgrade-the-adobe-campaign-server-application),
* [同步资源](#synchronize-resources),
* [重新启动服务](#restart-services)。

要了解如何更新客户端控制台，请参阅 [此部分](../../installation/using/client-console-availability-for-windows.md)。

### 关闭服务 {#shut-down-services}

要用新版本替换所有文件，您需要关闭nlserver服务的所有实例。

1. 关闭以下服务：

   * Web服务(IIS):

      **iisreset /stop**

   * Adobe Campaign服务： **net stop nlserver6**
   >[!IMPORTANT]
   >
   >您还需要确保重定向服务器(webmdl)已停止，以便 **IIS使用的nlsrvmod.dll** 文件可以替换为新版本。

1. 通过运行nlserver pdump命令检查没有任务 **处于活动状态** 。 应出现以下内容：

   ```
   C:<installation path>Adobe Campaign v7bin>nlserver pdump
   HH:MM:SS > Application Server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   No tasks
   ```

   您可以使用Windows任务管理器来确保所有进程都停止。

### 升级Adobe Campaign服务器应用程序 {#upgrade-the-adobe-campaign-server-application}

要运行升级文件，请应用以下步骤：

1. 运 **行setup.exe**。

   要下载此文件，请通过下载中心链接转 [到Adobe Campaign](https://support.neolane.net/)支持页 **面(https://support.neolane.net/** )。

1. 选择安装模式：选择 **[!UICONTROL Update or repair]**
1. 单击 **[!UICONTROL Next]** .
1. 单击 **[!UICONTROL Finish]** .

   安装项目随后将复制新文件。

1. 操作完成后，单击 **[!UICONTROL Finish]** 。

### 同步资源 {#synchronize-resources}

使用以下命令行：

**nlserver config -postupgrade -allinstances**

这将允许您执行以下操作：

* 同步资源、
* 更新模式,
* 更新数据库。

>[!NOTE]
>
>此操作只应执行一次，并且仅在(nlserver web)应&#x200B;**用程序服**&#x200B;务器上执行。

然后检查同步是否生成错误或警告。 有关此问题的详细信息，请参 [阅解决升级冲突](#resolving-upgrade-conflicts)。

### 重新启动服务 {#restart-services}

要重新启动的服务包括：

* Web服务(IIS):

   **iisreset /开始**

* Adobe Campaign服务： **网络开始nlserver6**

## Linux {#in-linux}

要在交付新版本时更新新版本中的Adobe Campaign,Linux的过程如下：

* [获取更新的包](#obtain-updated-packages),
* [执行更新](#perform-an-update),
* [重新启动Web服务器](#reboot-the-web-server)。

要了解如何更新客户端控制台，请参阅 [此部分](../../installation/using/client-console-availability-for-linux.md)。

>[!NOTE]
>
>从构建8757起，不再需要第三方库。

### 获取更新的包 {#obtain-updated-packages}

开始：通过恢复更新的Adobe Campaign包：通过下载中心链接转 [到Adobe Campaign](https://support.neolane.net/)支 **持页面(** https://support.neolane.net/)。

文件为 **nlserver6-v7-XXX.rpm**

### 执行更新 {#perform-an-update}

* 基于RPM的分发(RedHat、SuSe)

   要安装它们，请以root身份执行：

   ```
   $rpm -Uvh nlserver6-v7-XXXX.rpm
   ```

   其中XXX是文件的版本。

   rpm文件依赖于CentOS/Red Hat分发上的包。 如果您不想使用其中的某些依赖关系，则可能必须使用rpm的“nodeps”选项：

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
>本节详细介绍了完整 [的安装过程](../../installation/using/installing-campaign-standard-packages.md)。 资源会自动同步，但您需要确保未发生错误。 有关此问题的详细信息，请参 [阅解决升级冲突](#resolving-upgrade-conflicts)。

### 重新启动Web服务器 {#reboot-the-web-server}

必须关闭Apache才能使新库变得适用。

为此，请执行以下命令：

```
/etc/init.d/apache stop
```

>[!IMPORTANT]
>
>* 您的脚本可能称为 **httpd** ，而非 **apache**。
>* 您必须执行此命令，直到您获得以下回复：

   >
   >   
   此操作是Apache应用新库所必需的。


然后重新启动Apache:

```
/etc/init.d/apache start
```

## 解决升级冲突 {#resolving-upgrade-conflicts}

在资源同步过程中， **postupgrade** 命令允许您检测同步是否生成了错误或警告。

### 视图同步结果 {#view-the-synchronization-result}

有两种查看同步结果的方法：

* 在命令行接口中，错误由三个V形标记>> **实现** ，同步将自动停止。 警告由多次V形标记 **>>实** 现，并且必须在同步完成后解决。 在播放结束时，命令提示符下会显示一个摘要。 它可以如下：

   ```
   2013-04-09 07:48:39.749Z 00002E7A 1 info log =========Summary of the update==========
   2013-04-09 07:48:39.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   如果警告涉及资源冲突，则需要用户注意才能解决该问题。

* postupgrade **_`<server version number>_<time of postupgrade>`** .log日志文件包含同步结果。 默认情况下，它位于以下目录中： **`<installation directory>/var/<instance/postupgrade`**. 错误和警告由错误和警告属性指示。

### 解决冲突 {#resolving-conflicts}

要解决冲突，请应用以下流程：

1. 在Adobe Campaign树中，转到 **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]** 。
1. 在列表中选择要解决的冲突。

解决冲突有三种方法：

* **[!UICONTROL Declare as resolved]** :需要事先进行用户干预。
* **[!UICONTROL Accept the new version]** :如果用户未更改随Adobe Campaign提供的资源，则建议使用此选项。
* **[!UICONTROL Keep the current version]** :表示更新被拒绝。

   >[!IMPORTANT]
   >
   >如果选择此分辨率模式，您可能无法从新版本中的校正中受益。

如果选择手动解决冲突，请按如下方式继续：

1. 在窗口的下半部分，搜索冲突 **_字符串_** ，以查找存在冲突的实体。 随新版本一起安装的实体包 **含** new参数，与先前版本匹配的实体包含 **cus** 参数。

   ![](assets/s_ncs_production_conflict002.png)

1. 删除您不想保留的版本。 删除 **_要保留的实体_** conflict_argument字符串。

   ![](assets/s_ncs_production_conflict003.png)

1. 转到已解决的冲突。 单击图 **[!UICONTROL Actions]** 标并选择 **[!UICONTROL Declare as resolved]** 。
1. 保存更改：冲突现已解决。

### 最佳做法 {#best-practices}

更新失败可能链接到数据库配置。 确保技术管理员和数据库管理员执行的配置兼容。

例如，Unicode存储库不仅必须对LATIN1数据进行授权，等等。

## 警告客户端控制台可用的更新 {#warn-the-client-consoles-of-the-available-update}

### Windows {#in-windows-1}

在安装(nlserver web)**Adobe Campaign应用**&#x200B;程序服务器的计算机上，下载并复制文件

**setup-client-6.XXXX.exe**

**应[用程序的路径]**datakitnlengjsp

下次连接客户端控制台时，将显示一个窗口通知用户更新的可用性，并优惠用户下载和安装该更新的可能性。

>[!NOTE]
>
>确保IIS_XPG用户具有此安装文件的相应读取权限，并参阅安装 [指南](../../installation/using/general-architecture.md) ，了解详细信息。

### Linux {#in-linux-1}

在安装Adobe Campaign应用程序服务器(**nlserver web**)的计算机上，检索以下包：

**setup-client-6.XXXX.exe**

并复制它，另 **存为/usr/local/neolane/nl6/datakit/nl/eng/jsp**:

```
 cp setup-client-6.XXXX.exe /usr/local/neolane/nl6/datakit/nl/eng/jsp
```

下次连接客户端控制台时，将显示一个窗口通知用户更新的可用性，并优惠用户下载和安装该更新的可能性。

>[!NOTE]
>
>确保Apache用户具有适当的此安装文件读取权限，并参阅安 [装指南](../../installation/using/general-architecture.md) ，了解详细信息。

