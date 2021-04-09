---
solution: Campaign Classic
product: campaign
title: 配置 Campaign 服务器
description: 配置 Campaign 服务器
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
translation-type: tm+mt
source-git-commit: ae4f86f3703b9bfe7f08fd5c2580dd5da8c28cbd
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 2%

---

# 开始使用活动服务器配置{#gs-campaign-server-config}

本章详细介绍了可以执行以匹配您的需求和您的环境特性的服务器端配置。

## 限制

这些过程仅限于&#x200B;**内部部署**/**混合**&#x200B;部署，并需要管理权限。

对于&#x200B;**托管**&#x200B;部署，只能通过Adobe配置服务器端设置。 但是，可以在[活动控制面板](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html)中设置某些设置，如IP管允许列表理或URL权限。 [了解详情](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html)。

有关详细信息，请参阅以下部分：

* [控制面板文档](https://docs.adobe.com/content/help/zh-Hans/control-panel/using/control-panel-home.html)
* [托管模型](../../installation/using/hosting-models.md)
* [Campaign Classic本地和托管功能矩阵](../../installation/using/capability-matrix.md)

## 配置文件

Campaign Classic配置文件存储在Adobe Campaign安装文件夹的&#x200B;**conf**&#x200B;文件夹中。 配置分布在两个文件上：

* **serverConf.xml**:所有实例的常规配置。此文件结合了Adobe Campaign服务器的技术参数：这些属性由所有实例共享。 以下对这些参数的描述详尽。 此[节](../../installation/using/the-server-configuration-file.md)中列出的不同节点和参数。
* **config-`<instance>`.xml** (其中 **** instance是实例的名称):实例的特定配置。如果您在多个实例之间共享服务器，请在其相关文件中输入每个实例的特定参数。

## 配置范围

根据您的需要和配置，配置或调整活动服务器。 您可以：

* 保护[内部标识符](#internal-identifier)
* 启用[活动进程](#enabling-processes)
* 配置[URL权限](url-permissions.md)
* 定义[安全区域](security-zones.md)
* 配置[Tomcat设置](configure-tomcat.md)
* 自定义[投放参数](configure-delivery-settings.md)
* 定义[动态页面安全性和中继](#dynamic-page-security-and-relays)
* 限制[允许的外部命令](#restricting-authorized-external-commands)的列表
* 设置[冗余跟踪](#redundant-tracking)
* 管理[高可用性和工作流关联](#high-availability-workflows-and-affinities)
* 配置文件管理 — [了解更多](file-res-management.md)
   * 限制上载文件格式
   * 启用对公共资源的访问
   * 配置代理连接
* [自动进程重启](#automatic-process-restart)


## 内部标识符{#internal-identifier}

**internal**&#x200B;标识符是用于安装、管理和维护目的的技术登录名。 此登录与实例不关联。

使用此登录名连接的操作员将拥有所有实例的所有权限。 在安装新的情况下，此登录名将没有密码。 必须手动定义此密码。

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

## 启用进程{#enabling-processes}

服务器上的Adobe Campaign进程通过&#x200B;**config-default.xml**&#x200B;和&#x200B;**`config-<instance>.xml`**&#x200B;文件启用（并禁用）。

要将更改应用到这些文件，如果Adobe Campaign服务已启动，则必须运行&#x200B;**nlserver config -reload**&#x200B;命令。

有两种进程：多实例和单实例。

* **多实例**:为所有实例启动一个进程。**web**、**syslogd**&#x200B;和&#x200B;**trackinglogd**&#x200B;进程就是这种情况。

   可以从&#x200B;**config-default.xml**&#x200B;文件配置Enablement。

   声明Adobe Campaign服务器访问客户端控制台和重定向（跟踪）：

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   在此示例中，使用Linux中的&#x200B;**vi**&#x200B;命令编辑文件。 可以使用任何&#x200B;**.txt**&#x200B;或&#x200B;**.xml**&#x200B;编辑器进行编辑。

* **单实例**:每个实例(模块： **mta**、wfserver **、** inMail **、** **** sm **和** stat )。

   可以使用实例的配置文件配置启用：

   ```
   config-<instance>.xml
   ```

   声明服务器用于投放、执行工作流实例和恢复弹回邮件：

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

**活动存储**

您可以配置存储数据（日志、下载、重定向等）的Adobe Campaign目录（**var**&#x200B;目录）。 为此，请使用&#x200B;**XTK_VAR_DIR**&#x200B;系统变量：

* 在Windows中，在&#x200B;**XTK_VAR_DIR**&#x200B;系统变量中指示以下值

   ```
   D:\log\AdobeCampaign
   ```

* 在Linux中，转到&#x200B;**customer.sh**&#x200B;文件并指示：**导出XTK_VAR_DIR=/app/log/AdobeCampaign**。

   有关详细信息，请参阅[个性化参数](../../installation/using/installing-packages-with-linux.md#personalizing-parameters)。


## 动态页安全和中继{#dynamic-page-security-and-relays}

默认情况下，所有动态页都自动与启动Web模块的计算机的&#x200B;**local** Tomcat服务器相关。 此配置在&#x200B;**ServerConf.xml**&#x200B;文件的查询中继配置的&#x200B;**`<url>`**&#x200B;部分中输入。

您可以在&#x200B;**remote**&#x200B;服务器上中继动态页的执行；如果计算机上未激活Web模块。 为此，必须将&#x200B;**localhost**&#x200B;替换为JSP和JSSP、Web 应用程序、报表和字符串的远程计算机名称。

有关各种可用参数的详细信息，请参阅&#x200B;**serverConf.xml**&#x200B;配置文件。

对于JSP页，默认配置为：

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign使用以下JSP页：

* /nl/jsp/**soaprouter**:客户端控制台和Web服务连接(SOAP API),
* /nl/jsp/**mjsp**:镜像页面,
* /nl/jsp/**logon.jsp**:通过Web访问报告和客户端控制台的部署，
* /nl/jsp/**s.jsp**:使用病毒式营销（赞助和社交网络）。

用于移动应用程序渠道的JSSP如下：

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**示例:**

可以防止从外部连接客户机。 为此，只需限制&#x200B;**soaprouter.jsp**&#x200B;的执行，并仅授权执行镜像页面、病毒链接、Web表单和公共资源。

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

在此示例中，**`<IP_addresses>`**&#x200B;值与授权使用此掩码的中继模块的IP地址（以comas分隔）的列表一致。

>[!NOTE]
>
>值应根据您的配置和网络限制进行调整，尤其是在为您的安装开发了特定配置时。

### 管理HTTP头{#managing-http-headers}

默认情况下，不会中继所有HTTP头。 您可以在中继发送的回复中添加特定标头。 操作步骤：

1. 转到&#x200B;**serverConf.xml**&#x200B;文件。
1. 在&#x200B;**`<relay>`**&#x200B;节点中，转到中继HTTP头的列表。
1. 添加具有以下属性的&#x200B;**`<responseheader>`**&#x200B;元素：

   * **name**:标题名称
   * **值**:值名称。

   例如：

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 限制已授权的外部命令{#restricting-authorized-external-commands}

从内部版本8780起，技术管理员可以限制列表可在Adobe Campaign中使用的授权外部命令。

为此，您需要创建一个文本文件，其中列表有您要阻止使用的命令，例如：

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
>此列表并非详尽无遗。

在服务器配置文件的&#x200B;**exec**&#x200B;节点中，您需要引用&#x200B;**blacklistFile**&#x200B;属性中先前创建的文件。

**仅适用于Linux**:在服务器配置文件中，我们重命令您指定专用于执行外部命令的用户，以增强您的安全配置。此用户在配置文件的&#x200B;**exec**&#x200B;节点中设置。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

>[!NOTE]
>
>如果未指定任何用户，则在Adobe Campaign实例的用户上下文中执行所有命令。 用户必须与运行Adobe Campaign的用户不同。

例如：

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

此用户需要添加到“neolane”Adobe Campaign运算符的用户列表。

>[!IMPORTANT]
>
>您不应使用自定义sudo。 系统上需要安装标准sudo。


## 冗余跟踪{#redundant-tracking}

当多台服务器用于重定向时，它们必须能够通过SOAP调用相互通信，以共享来自要重定向的URL的信息。 在投放开始时，可能并非所有重定向服务器都可用；因此，他们可能没有同等级别的信息。

>[!NOTE]
>
>使用标准或企业架构时，必须授权主应用程序服务器在每台计算机上上传跟踪信息。

必须通过&#x200B;**serverConf.xml**&#x200B;文件在重定向配置中指定冗余服务器的URL。

**示例:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

**enableIf**&#x200B;属性是可选的（默认为空），并且仅在结果为true时允许您启用连接。 这样，您就可以在所有重定向服务器上获得相同的配置。

要获取计算机的主机名，请运行以下命令：**hostname -s**。



## 高可用性工作流和关联{#high-availability-workflows-and-affinities}

您可以配置多个工作流服务器(wfserver)，并将它们分发到两台或多台计算机上。 如果选择此类型的架构，请根据Adobe Campaign访问配置负载平衡器的连接模式。

要从Web访问，请选择&#x200B;**负载平衡器**&#x200B;模式以限制连接时间。

如果通过Adobe Campaign控制台访问，请选择&#x200B;**哈希**&#x200B;或&#x200B;**粘性ip**&#x200B;模式。 这样，您就可以保持富客户端与服务器之间的连接，并防止用户会话在导入或导出操作期间中断。

您可以选择强制在特定计算机上执行工作流或工作流活动。 为此，您必须为相关工作流或活动定义一个或多个关联。

1. 通过在&#x200B;**[!UICONTROL Affinity]**&#x200B;字段中输入工作流或活动的关联，创建这些。

   您可以选择任何关联名称，但请确保不使用空格或标点符号。 如果使用不同的服务器，请指定不同的名称。

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   下拉列表包含以前使用的关联。 它会随着时间的推移使用不同的输入值完成。

1. 打开&#x200B;**nl6/conf/config-`<instance>.xml`**&#x200B;文件。
1. 修改与&#x200B;**[!UICONTROL wfserver]**&#x200B;模块匹配的行，如下所示：

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   如果定义了多个关联，则必须用逗号分隔，不带任何空格：

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   执行未定义关联的工作流时，必须使用关联名称后面的逗号。

   如果您希望仅执行定义了关联的工作流，请不要在关联的列表末尾添加逗号。 例如，修改行，如下所示：

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## 自动重新启动{#automatic-process-restart}

默认情况下，不同的Adobe Campaign进程每天在早上6点（服务器时间）自动重新启动。

但是，您可以更改此配置。

要执行此操作，请转至安装的&#x200B;**conf**&#x200B;存储库中的&#x200B;**serverConf.xml**&#x200B;文件。

在此文件中配置的每个进程都具有&#x200B;**processRestartTime**&#x200B;属性。 您可以修改此属性的值，以根据您的需要调整每个进程的重新启动时间。

>[!IMPORTANT]
>
>请勿删除此属性。 必须每天重新启动所有进程。
