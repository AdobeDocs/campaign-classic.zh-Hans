---
product: campaign
title: 配置 Campaign 服务器
description: 配置 Campaign 服务器
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 3%

---

# Campaign服务器配置入门{#gs-campaign-server-config}

![](../../assets/v7-only.svg)

本章详细介绍可以执行以匹配您的需求和环境特性的服务器端配置。

## 限制

这些过程仅限于&#x200B;**on-premise**/**hybrid**&#x200B;部署，并需要管理权限。

对于托管的&#x200B;****&#x200B;部署，服务器端设置只能通过Adobe进行配置。 但是，某些设置可以在[促销活动控制面板](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hans)中设置，例如IP允许列表管理或URL权限。 [了解详情](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=zh-Hans)。

有关更多信息，请参阅以下章节：

* [控制面板文档](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hans)
* [托管模型](../../installation/using/hosting-models.md)
* [Campaign Classic本地和托管功能矩阵](../../installation/using/capability-matrix.md)

## 配置文件

Campaign Classic配置文件存储在Adobe Campaign安装文件夹的&#x200B;**conf**&#x200B;文件夹中。 配置分布在两个文件上：

* **serverConf.xml**:所有实例的常规配置。此文件结合了Adobe Campaign服务器的技术参数：这些实例由所有实例共享。 下面详细介绍了其中一些参数。 此[部分](../../installation/using/the-server-configuration-file.md)中列出的不同节点和参数。
* **config-`<instance>`.xml** (其中 **** 实例是实例的名称):实例的特定配置。如果您在多个实例之间共享服务器，请在其相关文件中输入特定于每个实例的参数。

## 配置范围

根据您的需求和配置，配置或调整Campaign服务器。 您可以：

* 保护[内部标识符](#internal-identifier)
* 启用[Campaign进程](#enabling-processes)
* 配置[URL权限](url-permissions.md)
* 定义[安全区](security-zones.md)
* 配置[Tomcat设置](configure-tomcat.md)
* 自定义[投放参数](configure-delivery-settings.md)
* 定义[动态页面安全性和中继](#dynamic-page-security-and-relays)
* 限制[允许的外部命令列表](#restricting-authorized-external-commands)
* 设置[冗余跟踪](#redundant-tracking)
* 管理[高可用性和工作流相关性](#high-availability-workflows-and-affinities)
* 配置文件管理 — [了解详情](file-res-management.md)
   * 限制上载文件格式
   * 启用对公共资源的访问
   * 配置代理连接
* [自动进程重新启动](#automatic-process-restart)


## 内部标识符 {#internal-identifier}

**internal**&#x200B;标识符是用于安装、管理和维护的技术登录名。 此登录与实例不关联。

使用此登录名连接的操作员将拥有所有实例的所有权限。 如果安装了新安装，此登录将没有密码。 您必须手动定义此密码。

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

通过&#x200B;**config-default.xml**&#x200B;和&#x200B;**`config-<instance>.xml`**&#x200B;文件，可启用（并禁用）服务器上的Adobe Campaign进程。

要将更改应用到这些文件，如果启动了Adobe Campaign服务，则必须运行&#x200B;**nlserver config -reload**&#x200B;命令。

流程有两种类型：多实例和单实例。

* **多实例**:所有实例都会启动一个进程。**web**、**syslogd**&#x200B;和&#x200B;**trackinglogd**&#x200B;进程就是这样。

   可以从&#x200B;**config-default.xml**&#x200B;文件中配置启用。

   声明Adobe Campaign服务器访问客户端控制台并进行重定向（跟踪）：

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   在本例中，使用Linux中的&#x200B;**vi**&#x200B;命令编辑文件。 可以使用任何&#x200B;**.txt**&#x200B;或&#x200B;**.xml**&#x200B;编辑器进行编辑。

* **单实例**:每个实例启动一个进程(模块： **mta**、 **wfserver**、 **inMail**、 **** sms **stat**)。

   可以使用实例的配置文件配置启用：

   ```
   config-<instance>.xml
   ```

   声明服务器以进行投放、执行工作流实例和恢复退回邮件：

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

**营销活动数据存储**

您可以配置Adobe Campaign数据（日志、下载、重定向等）的存储目录（**var**&#x200B;目录）。 要实现此目的，请使用&#x200B;**XTK_VAR_DIR**&#x200B;系统变量：

* 在Windows中，在&#x200B;**XTK_VAR_DIR**&#x200B;系统变量中指示以下值

   ```
   D:\log\AdobeCampaign
   ```

* 在Linux中，转到&#x200B;**customer.sh**&#x200B;文件并指示：**导出XTK_VAR_DIR=/app/log/AdobeCampaign**。

   有关更多信息，请参阅[个性化参数](../../installation/using/installing-packages-with-linux.md#personalizing-parameters)。


## 动态页面安全和中继 {#dynamic-page-security-and-relays}

默认情况下，所有动态页面都自动与启动Web模块的计算机的&#x200B;**本地** Tomcat服务器相关联。 此配置在&#x200B;**ServerConf.xml**&#x200B;文件的查询中继配置的&#x200B;**`<url>`**&#x200B;部分中输入。

您可以在&#x200B;**remote**&#x200B;服务器上中继动态页面的执行；未在计算机上激活Web模块时。 要实现此目的，必须将&#x200B;**localhost**&#x200B;替换为JSP和JSSP、Web应用程序、报告和字符串的远程计算机的名称。

有关各种可用参数的更多信息，请参阅&#x200B;**serverConf.xml**&#x200B;配置文件。

对于JSP页，默认配置为：

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign使用以下JSP页：

* /nl/jsp/**soaprouter.jsp**:客户端控制台和Web服务连接(SOAP API)、
* /nl/jsp/**m.jsp**:镜像页面，
* /nl/jsp/**logon.jsp**:通过Web访问报告和部署客户端控制台，
* /nl/jsp/**s.jsp** :使用病毒式营销（赞助和社交网络）。

用于移动设备应用程序渠道的JSSP如下所示：

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**示例:**

可以阻止从外部连接客户机。 为此，只需限制&#x200B;**soaprouter.jsp**&#x200B;的执行，并仅授权执行镜像页面、病毒链接、Web窗体和公共资源。

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

在此示例中，**`<IP_addresses>`**&#x200B;值与有权使用此掩码的中继模块的IP地址列表（由comas分隔）一致。

>[!NOTE]
>
>值应根据您的配置和网络限制进行调整，特别是当已为您的安装开发了特定配置时。

### 管理HTTP头 {#managing-http-headers}

默认情况下，不会中继所有HTTP标头。 您可以在中继发送的回复中添加特定的标头。 操作步骤：

1. 转到&#x200B;**serverConf.xml**&#x200B;文件。
1. 在&#x200B;**`<relay>`**&#x200B;节点中，转到中继HTTP头的列表。
1. 添加具有以下属性的&#x200B;**`<responseheader>`**&#x200B;元素：

   * **名称**:标题名称
   * **值**:值名称。

   例如：

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 限制授权的外部命令 {#restricting-authorized-external-commands}

从版本8780开始，技术管理员可以限制可在Adobe Campaign中使用的授权外部命令列表。

为此，您需要创建一个文本文件，其中包含您要阻止使用的命令列表，例如：

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
>此列表并不详尽。

在服务器配置文件的&#x200B;**exec**&#x200B;节点中，您需要引用之前在&#x200B;**blacklistFile**&#x200B;属性中创建的文件。

**仅适用于Linux**:在服务器配置文件中，我们建议您指定一个专门执行外部命令的用户来增强您的安全配置。此用户在配置文件的&#x200B;**exec**&#x200B;节点中设置。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

>[!NOTE]
>
>如果未指定用户，则所有命令都将在Adobe Campaign实例的用户上下文中执行。 用户必须与运行Adobe Campaign的用户不同。

例如：

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

需要将此用户添加到“neolane”Adobe Campaign运算符的子列表。

>[!IMPORTANT]
>
>您不应使用自定义sudo。 系统上需要安装标准sudo。


## 冗余跟踪 {#redundant-tracking}

当使用多个服务器进行重定向时，它们必须能够通过SOAP调用彼此通信，以便共享要重定向的URL中的信息。 在投放启动时，并非所有重定向服务器都可用；因此，他们可能没有相同级别的信息。

>[!NOTE]
>
>使用标准架构或企业架构时，必须授权主应用程序服务器在每台计算机上上传跟踪信息。

必须通过&#x200B;**serverConf.xml**&#x200B;文件在重定向配置中指定冗余服务器的URL。

**示例:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

**enableIf**&#x200B;属性是可选的（默认为空），并且仅在结果为true时才允许您启用连接。 这样，您就可以在所有重定向服务器上获得相同的配置。

要获取计算机的主机名，请运行以下命令：**主机名 — s**。



## 高可用性工作流和相关性 {#high-availability-workflows-and-affinities}

您可以配置多个工作流服务器(wfserver)，并在两台或多台计算机上分发它们。 如果选择此类型的架构，请根据Adobe Campaign访问配置负载平衡器的连接模式。

要从Web访问，请选择&#x200B;**负载平衡器**&#x200B;模式以限制连接时间。

如果通过Adobe Campaign控制台访问，请选择&#x200B;**hash**&#x200B;或&#x200B;**置顶ip**&#x200B;模式。 这样，您就可以维护富客户端与服务器之间的连接，并防止用户会话在导入或导出操作期间中断。

您可以选择在特定计算机上强制执行工作流或工作流活动。 要实现此目的，您必须为相关工作流或活动定义一个或多个相关性。

1. 通过在&#x200B;**[!UICONTROL Affinity]**&#x200B;字段中输入工作流或活动的喜好来创建它们。

   您可以选择任何亲和度名称，但请确保不使用空格或标点符号。 如果您使用的服务器不同，请指定不同的名称。

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   下拉列表包含以前使用的相关性。 它会随着时间的推移使用不同的输入值完成。

1. 打开&#x200B;**nl6/conf/config-`<instance>.xml`**&#x200B;文件。
1. 修改与&#x200B;**[!UICONTROL wfserver]**&#x200B;模块匹配的行，如下所示：

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   如果定义多个喜好，则必须用逗号分隔，不留任何空格：

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   执行未定义亲和度的工作流时，必须使用关联名称后面的逗号。

   如果您只想执行定义了亲和度的工作流，请不要在亲和度列表的末尾添加逗号。 例如，按如下方式修改行：

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## 自动重新启动 {#automatic-process-restart}

默认情况下，不同的Adobe Campaign进程每天早上6点（服务器时间）自动重新启动。

但是，您可以更改此配置。

为此，请转到安装&#x200B;**conf**&#x200B;存储库中的&#x200B;**serverConf.xml**&#x200B;文件。

在此文件中配置的每个进程都具有&#x200B;**processRestartTime**&#x200B;属性。 您可以修改此属性的值，以根据需要调整每个进程的重新启动时间。

>[!IMPORTANT]
>
>请勿删除此属性。 必须每天重新启动所有进程。
