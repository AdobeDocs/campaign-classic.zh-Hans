---
product: campaign
title: 配置 Campaign 服务器
description: 配置 Campaign 服务器
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于Campaign Classicv7"
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1603'
ht-degree: 3%

---

# Campaign服务器配置入门{#gs-campaign-server-config}



本章详细介绍可根据您的需求和环境特性执行的服务器端配置。

## 限制

这些过程仅限于 **内部部署**/**混合** 部署并需要管理权限。

对象 **托管** 部署、服务器端设置只能由Adobe配置。 但是，可以在中设置某些设置 [营销活动控制面板](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hans)，如IP允许列表管理或URL权限。 [了解详情](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=zh-Hans)。

有关更多信息，请参阅以下章节：

* [控制面板文档](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hans)
* [托管模型](../../installation/using/hosting-models.md)
* [Campaign Classic本地和托管功能表](../../installation/using/capability-matrix.md)

## 配置文件

Campaign Classic配置文件存储在 **会议** Adobe Campaign安装文件夹的文件夹。 该配置分为两个文件：

* **serverConf.xml**：所有实例的常规配置。 此文件结合了Adobe Campaign服务器的技术参数：这些参数由所有实例共享。 下面详细描述了其中一些参数。 本中列出的不同节点和参数 [部分](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (其中 **实例** 实例的名称)：实例的特定配置。 如果在多个实例之间共享服务器，请在相关文件中输入特定于每个实例的参数。

## 配置范围

根据您的需求和配置配置配置或调整Campaign服务器。 您可以：

* 保护 [内部标识符](#internal-identifier)
* 启用 [营销活动流程](#enabling-processes)
* 配置 [URL权限](url-permissions.md)
* 定义 [安全区域](security-zones.md)
* 配置 [Tomcat设置](configure-tomcat.md)
* 自定义 [投放参数](configure-delivery-settings.md)
* 定义 [动态页面安全和中继](#dynamic-page-security-and-relays)
* 限制列表 [允许的外部命令](#restricting-authorized-external-commands)
* 设置 [冗余跟踪](#redundant-tracking)
* 管理 [高可用性和工作流相关性](#high-availability-workflows-and-affinities)
* 配置文件管理 —  [了解详情](file-res-management.md)
   * 限制上载文件格式
   * 启用对公共资源的访问
   * 配置代理连接
* [流程自动重新启动](#automatic-process-restart)


## 内部标识符 {#internal-identifier}

此 **内部** identifier是用于安装、管理和维护的技术登录。 此登录名未与实例关联。

使用此登录进行连接的操作员将拥有所有实例的所有权限。 如果是新安装，此登录将没有密码。 您必须手动定义此密码。

使用以下命令：

```
nlserver config -internalpassword
```

随后将显示以下信息。 输入并确认密码：

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## 启用进程 {#enabling-processes}

通过启用（和禁用）服务器上的Adobe Campaign进程 **config-default.xml** 和 **`config-<instance>.xml`** 文件。

要将更改应用到这些文件，如果Adobe Campaign服务已启动，则必须运行 **nlserver配置 — reload** 命令。

有两种类型的进程：多实例和单实例。

* **多实例**：为所有实例启动一个进程。 这就是 **Web**， **syslogd** 和 **trackinglogd** 进程。

  可以从以下位置配置启用 **config-default.xml** 文件。

  声明Adobe Campaign服务器以访问客户端控制台并进行重定向（跟踪）：

  ```
  vi nl6/conf/config-default.xml
  <web args="-tomcat" autoStart="true"/>  
  <!-- to start if the machine is also a redirection server -->  
  <trackinglogd autoStart="true"/>
  ```

  在此示例中，使用编辑文件 **vi** 命令。 可以使用任何 **.txt** 或 **.xml** 编辑者。

* **单实例**：为每个实例启动一个进程(模块： **mta**， **wfserver**， **inMail**， **短信** 和 **stat**)。

  可使用实例的配置文件配置启用：

  ```
  config-<instance>.xml
  ```

  声明要交付的服务器，执行工作流实例并恢复退回邮件：

  ```
  <mta autoStart="true" statServerAddress="localhost"/>
  <wfserver autoStart="true"/>  
  <inMail autoStart="true"/>
  <stat autoStart="true"/>
  ```

**Campaign数据存储**

您可以配置存储目录(**变量** Adobe Campaign目录)执行相同的更改（日志、下载、重定向等）。 要执行此操作，请使用 **XTK_VAR_DIR** 系统变量：

* 在Windows中，在 **XTK_VAR_DIR** 系统变量

  ```
  D:\log\AdobeCampaign
  ```

* 在Linux中，转到 **customer.sh** 文件并指示： **export XTK_VAR_DIR=/app/log/AdobeCampaign**.

  有关详细信息，请参见 [个性化参数](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## 动态页面安全和中继 {#dynamic-page-security-and-relays}

默认情况下，所有动态页面都会自动与 **本地** 已启动Web模块的计算机的Tomcat服务器。 此配置输入于 **`<url>`** 的查询中继配置的部分 **ServerConf.xml** 文件。

您可以在中继页面上执行动态页面， **远程** 服务器；如果计算机上未激活Web模块。 为此，您必须将 **localhost** 远程计算机的名称，用于JSP和JSSP、Web应用程序、报告和字符串。

有关各种可用参数的更多信息，请参阅 **serverConf.xml** 配置文件。

对于JSP页，默认配置为：

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign使用以下JSP页：

* /nl/jsp/**soaprouter.jsp**：客户端控制台和Web服务连接(SOAP API)、
* /nl/jsp/**m.jsp**：镜像页面，
* /nl/jsp/**logon.jsp**：基于Web访问报告和部署客户端控制台，
* /nl/jsp/**s.jsp** ：使用病毒式营销（赞助和社交网络）。

用于移动设备应用程序渠道的JSSP如下所示：

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**示例:**

可以防止从外部进行客户端计算机连接。 要实现此目的，只需限制执行 **soaprouter.jsp** 并且仅授权执行镜像页面、病毒链接、Web窗体和公共资源。

参数如下：

```
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/> 
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="m.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="s.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="webForm.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/webApp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/jssp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/strings/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/interaction/pub*"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/>
```

在此示例中， **`<IP_addresses>`** 值与授权使用此掩码的中继模块的IP地址列表（以逗号分隔）一致。

>[!NOTE]
>
>应根据您的配置和网络限制调整值，尤其是在已经为您的安装开发了特定配置的情况下。

### 管理HTTP标头 {#managing-http-headers}

默认情况下，不会中继所有HTTP标头。 您可以在由中继发送的回复中添加特定标头。 操作步骤：

1. 转到 **serverConf.xml** 文件。
1. 在 **`<relay>`** 节点，转到中继HTTP标头的列表。
1. 添加 **`<responseheader>`** 元素具有以下属性：

   * **name**：标题名称
   * **值**：值名称。

   例如：

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 限制授权的外部命令 {#restricting-authorized-external-commands}

从版本8780开始，技术管理员可以限制可在Adobe Campaign中使用的授权外部命令列表。

为此，您需要创建一个文本文件，其中包含要阻止使用的命令列表，例如：

```
ln
dd
openssl
curl
wget
python
python3
perl
ruby
sh
```

>[!IMPORTANT]
>
>这份清单并非详尽无遗。

在 **执行** 节点时，您需要在 **blacklistFile** 属性。

**仅适用于Linux**：在服务器配置文件中，建议您指定专门用于执行外部命令的用户来增强安全配置。 此用户在 **执行** 配置文件的节点。 中所有可用的参数，请参见 **serverConf.xml** 中列出 [部分](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>如果未指定用户，则所有命令都将在Adobe Campaign实例的用户上下文中执行。 该用户必须不同于运行Adobe Campaign的用户。

例如：

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

需要将此用户添加到“neolane”Adobe Campaign运算符的sudoer列表。

>[!IMPORTANT]
>
>您不应使用自定义sudo。 系统需要安装标准的sudo。


## 冗余跟踪 {#redundant-tracking}

当使用多个服务器进行重定向时，它们必须能够通过SOAP调用相互通信，以便共享要重定向的URL中的信息。 在投放启动时，可能并非所有重定向服务器都可用；因此，它们可能没有相同级别的信息。

>[!NOTE]
>
>在使用标准或企业体系结构时，必须授权主应用程序服务器在每台计算机上上载跟踪信息。

必须在重定向配置中通过指定冗余服务器的URL **serverConf.xml** 文件。

**示例:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

此 **enableIf** 属性是可选的（默认情况下为空），并且仅在结果为true时才允许您启用连接。 这使您可以在所有的重定向服务器上获得相同的配置。

要获取计算机的主机名，请运行以下命令： **主机名 — s**.



## 高可用性工作流和任务共用性 {#high-availability-workflows-and-affinities}

您可以配置多个工作流服务器(wfserver)并在两台或多台计算机上分发它们。 如果选择此类型的体系结构，请根据Adobe Campaign访问配置负载平衡器的连接模式。

要从Web访问，请选择 **负载平衡器** 模式以限制连接时间。

如果通过Adobe Campaign控制台访问，请选择 **哈希** 或 **粘性ip** 模式。 这可以让您维护富客户端与服务器之间的连接，并防止用户会话在导入或导出操作期间中断，例如。

您可以选择在特定计算机上强制执行工作流或工作流活动。 要实现此目的，您必须为相关工作流或活动定义一个或多个任务共用性。

1. 通过在以下位置输入工作流或活动的任务共用性： **[!UICONTROL Affinity]** 字段。

   您可以选择任何关联名称，但请确保不使用空格或标点符号。 如果使用不同的服务器，请指定不同的名称。

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   下拉列表包含以前使用的任务共用性。 它会随着时间的推移使用不同的输入值完成。

1. 打开 **nl6/conf/config-`<instance>.xml`** 文件。
1. 修改与 **[!UICONTROL wfserver]** 模块如下所示：

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   如果定义多个相关性，则必须用逗号分隔它们，且不含任何空格：

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   执行未定义关联的工作流时，关联名称后面的逗号是必需的。

   如果您希望仅执行为其定义了关联的工作流，请不要在关联列表的末尾添加逗号。 例如，按如下方式修改该行：

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## 自动重新启动 {#automatic-process-restart}

默认情况下，不同的Adobe Campaign进程会在每天早上6点（服务器时间）自动重新启动。

但是，您可以更改此配置。

为此，请转到 **serverConf.xml** 文件，位于 **会议** 安装的存储库。

在此文件中配置的每个进程都有一个 **processRestartTime** 属性。 您可以修改此属性的值，以根据需要调整每个进程的重新启动时间。

>[!IMPORTANT]
>
>请勿删除此属性。 必须每天重新启动所有进程。
