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
source-git-commit: 0c83c989c7e3718a989a4943f5cde7ad4717fddc
workflow-type: tm+mt
source-wordcount: '2810'
ht-degree: 6%

---

# 配置 Campaign 服务器{#configuring-campaign-server}

以下部分详细介绍了可以执行以匹配您的需求和您的环境特性的服务器端配置。

这些配置必须由管理员执行，并且仅适用于&#x200B;**内部部署**&#x200B;托管模型。

对于&#x200B;**托管**&#x200B;部署，只能通过Adobe配置服务器端设置。 但是，可以在控制面板中设置某些设置(例如，IP管允许列表理或URL权限)。

>[!NOTE]
>
>所有管理员用户都可访问控制面板。[此部分](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hans#discover-control-panel)将详细介绍授予用户管理员访问权限的步骤。
>
>请注意，您的实例必须托管在AWS上，并使用最新的[Gold Standard](../../rn/using/gs-overview.md)版本或最新的[ GA版本(21.1)](../../rn/using/latest-release.md)进行升级。 了解如何在[本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中检查您的版本。 要检查您的实例是否托管在AWS上，请按照[本页](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)中详细介绍的步骤操作。

有关详细信息，请参阅以下部分：

* [控制面板文档](https://docs.adobe.com/content/help/zh-Hans/control-panel/using/control-panel-home.html)
* [托管模型](../../installation/using/hosting-models.md)
* [Campaign Classic本地和托管功能矩阵](../../installation/using/capability-matrix.md)
* [混合和托管模型配置步骤](../../installation/using/hosting-models.md)

Campaign Classic配置文件存储在Adobe Campaign安装文件夹的&#x200B;**conf**&#x200B;文件夹中。 配置分布在两个文件上：

* **serverConf.xml**:所有实例的常规配置。此文件结合了Adobe Campaign服务器的技术参数：这些属性由所有实例共享。 以下对这些参数的描述详尽。 此[节](../../installation/using/the-server-configuration-file.md)中列出的不同节点和参数。
* **config-`<instance>`.xml** (其中 **** instance是实例的名称):实例的特定配置。如果您在多个实例之间共享服务器，请在其相关文件中输入每个实例的特定参数。

## 配置Tomcat {#configuring-tomcat}

### Tomcat {#default-port-for-tomcat}的默认端口

当Tomcat服务器的8080侦听端口已忙于配置所需的其他应用程序时，您需要将8080端口替换为免费端口（例如8090）。 要更改它，请编辑保存在Adobe Campaign安装文件夹&#x200B;**/tomcat-8/conf**&#x200B;目录中的&#x200B;**server.xml**&#x200B;文件。

然后修改JSP中继页的端口。 为此，请更改保存在Adobe Campaign安装目录&#x200B;**/conf**&#x200B;目录中的&#x200B;**serverConf.xml**&#x200B;文件。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

### 在Tomcat {#mapping-a-folder-in-tomcat}中映射文件夹

要定义客户特定设置，可在&#x200B;**/tomcat-8/conf**&#x200B;文件夹中创建&#x200B;**user_上下文s.xml**&#x200B;文件，该文件中还包含&#x200B;**上下文.xml**&#x200B;文件。

此文件将包含以下类型的信息：

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

如有必要，可以在服务器端重现此操作。

## 个性化投放参数{#personalizing-delivery-parameters}

投放参数在&#x200B;**serverConf.xml**&#x200B;配置文件中定义。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

[活动服务器配置](../../installation/using/campaign-server-configuration.md)中详细介绍了常规服务器配置和命令。

您还可以根据您的需要和设置执行以下配置。

### SMTP中继{#smtp-relay}

MTA模块充当SMTP广播（端口25）的本机邮件传输代理。

但是，如果您的安全策略需要，则可以用中继服务器替换它。 在这种情况下，全局吞吐量将是中继吞吐量(前提是中继服务器吞吐量低于Adobe Campaign吞吐量)。

在这种情况下，通过在&#x200B;**`<relay>`**&#x200B;部分配置SMTP服务器来设置这些参数。 必须指定用于传输邮件的SMTP服务器的IP地址（或主机）及其关联端口（默认为25）。

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>这种操作模式对投放造成了严重的限制，因为由于中继服务器的固有性能（延迟、带宽……），它可以大大降低吞吐量。 此外，限定同步投放错误（通过分析SMTP流量检测到）的容量将受到限制，并且如果中继服务器不可用，则发送将不可能。

### MTA子进程{#mta-child-processes}

可以根据服务器的CPU功率和可用网络资源控制子进程（默认为2）的数量，以优化广播性能。 此配置将在每台计算机的MTA配置的&#x200B;**`<master>`**&#x200B;部分中进行。

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

另请参阅[电子邮件发送优化](../../installation/using/email-deliverability.md#email-sending-optimization)。

### 使用关联{#managing-outbound-smtp-traffic-with-affinities}管理出站SMTP通信

>[!IMPORTANT]
>
>关联配置需要从一台服务器到另一台服务器一致。 我们建议您与Adobe联系以进行关联配置，因为应在运行MTA的所有应用程序服务器上复制配置更改。

您可以通过具有IP地址的关联改善出站SMTP通信。

为此，请应用以下步骤：

1. 在&#x200B;**serverConf.xml**&#x200B;文件的&#x200B;**`<ipaffinity>`**&#x200B;部分输入关联。

   一个关联可以有多个不同的名称：要分离它们，请使用&#x200B;**;**&#x200B;字符。

   示例:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   要视图相关参数，请参阅&#x200B;**serverConf.xml**&#x200B;文件。

1. 要在下拉列表中启用关联选择，您需要在&#x200B;**IPAffinity**&#x200B;明细列表中添加关联名称。

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >明细列表详见[此文档](../../platform/using/managing-enumerations.md)。

   然后，您可以选择要使用的关联，如下所示，适用于类型：

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >您还可以引用[投放服务器配置](../../installation/using/email-deliverability.md#delivery-server-configuration)。

## URL 权限 {#url-permissions}

Campaign Classic 实例可以通过 JavaScript 代码（工作流等）调用的 URL 默认列表是有限的。这些 URL 允许实例正常运行。

默认情况下，实例不允许连接到外部 URL。但是，可以向授权URL的列表添加一些外部URL，以便您的实例可以连接到它们。 这允许您将 Campaign 实例连接到外部系统，例如 SFTP 服务器或网站，以启用文件和/或数据传输。

添加 URL 后，该 URL 将在实例的配置文件 (serverConf.xml) 中引用。

它们取决于您的托管模型：

* **** Hybridor **内部部署**:将允许的URL添加 **到serverConf.xml文件中**。详细信息请参阅以下部分。
* **托管**:添加允许通过控制面板的 **URL**。有关详细信息，请参阅[专用文档](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/url-permissions.html)。

   >[!NOTE]
   >
   >所有管理员用户都可访问控制面板。[此部分](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel)将详细介绍授予用户管理员访问权限的步骤。
   >
   >请注意，您的实例必须托管在AWS上，并使用最新的[Gold Standard](../../rn/using/gs-overview.md)版本进行升级。 了解如何在[本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中检查您的版本。 要检查您的实例是否托管在AWS上，请按照[本页](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)中详细介绍的步骤操作。

对于&#x200B;**Hybrid**&#x200B;和&#x200B;**On-premise**&#x200B;托管模型，管理员需要在&#x200B;**serverConf.xml**&#x200B;文件中引用新的&#x200B;**urlPermission**。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

存在三种连接保护模式：

* **阻止**:将阻止所有不属于该允许列表程序的URL，并显示错误消息。这是配置升级后的默认模式。
* **允许**:允许所有不属于该允许列表的URL。
* **警告**:允许所有不属于该程序允许列表的URL，但JS解释程序会发出警告，以便管理员可以收集这些URL。此模式添加JST-310027警告消息。

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>默认情况下，新客户的客户端使用&#x200B;**阻止模式**。 如果需要允许新URL，则应联系管理员以将其添加到允许列表。
>
>迁移中的现有客户可以使用&#x200B;**警告模式**&#x200B;一段时间。 同时，在对URL授权之前，他们需要分析出站流量。 定义授权URL的列表后，应联系其管理员，将URL添加允许列表到并激活&#x200B;**阻止模式**。

## 动态页安全和中继{#dynamic-page-security-and-relays}

默认情况下，所有动态页都自动与启动Web模块的计算机的&#x200B;**local** Tomcat服务器相关。 此配置在&#x200B;**ServerConf.xml**&#x200B;文件的查询中继配置的&#x200B;**`<url>`**&#x200B;部分中输入。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

在&#x200B;**remote**&#x200B;服务器上中继动态页的执行；如果计算机上未激活Web模块。 为此，必须将&#x200B;**localhost**&#x200B;替换为JSP和JSSP、Web 应用程序、报表和字符串的远程计算机名称。

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

## 限制已授权的外部命令{#restricting-authorized-external-commands}

>[!NOTE]
>
>仅内部部署安装需要以下配置。

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

## 管理HTTP头{#managing-http-headers}

默认情况下，不会中继所有HTTP头。 您可以在中继发送的回复中添加特定标头。 操作步骤：

1. 转到&#x200B;**serverConf.xml**&#x200B;文件。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。
1. 在&#x200B;**`<relay>`**&#x200B;节点中，转到中继HTTP头的列表。
1. 添加具有以下属性的&#x200B;**`<responseheader>`**&#x200B;元素：

   * **name**:标题名称
   * **值**:值名称。

   例如：

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## 冗余跟踪{#redundant-tracking}

当多台服务器用于重定向时，它们必须能够通过SOAP调用相互通信，以共享来自要重定向的URL的信息。 在投放开始时，可能并非所有重定向服务器都可用；因此，他们可能没有同等级别的信息。

>[!NOTE]
>
>使用标准或企业架构时，必须授权主应用程序服务器在每台计算机上上传跟踪信息。

必须通过&#x200B;**serverConf.xml**&#x200B;文件在重定向配置中指定冗余服务器的URL。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

**示例:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

**enableIf**&#x200B;属性是可选的（默认为空），并且仅在结果为true时允许您启用连接；这样，您就可以在所有重定向服务器上获得相同的配置。

要获取计算机的主机名，请运行以下命令：**hostname -s**。

## 管理公共资源{#managing-public-resources}

公共资源显示在[管理公共资源](../../installation/using/deploying-an-instance.md#managing-public-resources)中。

它们存储在Adobe Campaign安装目录的&#x200B;**/var/res/instance**&#x200B;目录中。

匹配的URL为：**http://server/res/instance**&#x200B;其中&#x200B;**instance**&#x200B;是跟踪实例的名称。

可以通过向&#x200B;**conf-`<instance>`.xml**&#x200B;文件添加节点来指定另一个目录，以在服务器上配置存储。 这意味着添加以下行：

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

在这种情况下，部署向导窗口上半部分中提供的公共资源的新URL应指向此文件夹。

## 高可用性工作流和关联{#high-availability-workflows-and-affinities}

您可以配置多个工作流服务器(wfserver)，并将它们分发到两台或多台计算机上。 如果选择此类型的架构，请根据Adobe Campaign访问配置负载平衡器的连接模式。

要从Web访问，请选择&#x200B;**负载平衡器**&#x200B;模式以限制连接时间。

如果通过Adobe Campaign控制台访问，请选择&#x200B;**哈希**&#x200B;或&#x200B;**粘性ip**&#x200B;模式。 这样，您就可以保持富客户端与服务器之间的连接，并防止用户会话在导入或导出操作期间中断。

您可以选择强制在特定计算机上执行工作流或工作流活动。 为此，您必须为相关工作流或活动定义一个或多个关联。

1. 通过在&#x200B;**[!UICONTROL Affinity]**&#x200B;字段中输入工作流或活动的关联，创建这些。

   您可以自由选择关联名称。 但是，请确保不使用空格或标点符号。 如果使用不同的服务器，请指定不同的名称。

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

## 自动进程重启{#automatic-process-restart}

默认情况下，不同的Adobe Campaign进程每天在早上6点（服务器时间）自动重新启动。

但是，您可以更改此配置。

要执行此操作，请转至安装的&#x200B;**conf**&#x200B;存储库中的&#x200B;**serverConf.xml**&#x200B;文件。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

在此文件中配置的每个进程都具有&#x200B;**processRestartTime**&#x200B;属性。 您可以修改此属性的值，以根据您的需要调整每个进程的重新启动时间。

>[!IMPORTANT]
>
>请勿删除此属性。 必须每天重新启动所有进程。

## 限制可上载文件{#limiting-uploadable-files}

新属性&#x200B;**uploadWhiteList**&#x200B;允许您限制可在Adobe Campaign服务器上上传的文件类型。

此属性在&#x200B;**serverConf.xml**&#x200B;文件的&#x200B;**dataStore**&#x200B;元素中可用。 **serverConf.xml**&#x200B;中可用的所有参数都列在此[部分](../../installation/using/the-server-configuration-file.md)中。

此属性的默认值为&#x200B;**。+**，它允许您上传任何文件类型。

要限制可能的格式，必须用有效的java常规表达式替换属性值。 可以通过用逗号分隔多个值。

例如：**uploadWhiteList=&quot;。*.png，.*.jpg&quot;**&#x200B;允许您在服务器上上传PNG和JPG格式。 不接受其他格式。

>[!IMPORTANT]
>
>在Internet Explorer中，完整的文件路径必须由常规表达式验证。

## 代理连接配置{#proxy-connection-configuration}

例如，可以使用&#x200B;**文件传输**&#x200B;工作流活动，将活动服务器通过代理连接到外部系统。 为此，您需要通过特定命令配置&#x200B;**serverConf.xml**&#x200B;文件的&#x200B;**proxyConfig**&#x200B;部分。 **serverConf.xml**&#x200B;中可用的所有参数均列在此[部分](../../installation/using/the-server-configuration-file.md)中。

可以使用以下代理连接：HTTP、HTTPS、FTP、SFTP。 请注意，从20.2活动版本开始，HTTP和HTTPS协议参数&#x200B;**不再可用**。 这些参数在以前的版本（包括9032）中仍然可用，因此下文仍提及。

>[!CAUTION]
>
>仅支持基本身份验证模式。 不支持NTLM身份验证。
>
>不支持SOCKS代理。


可以使用以下命令：

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

协议参数可以是“http”、“https”或“ftp”。

如果要将FTP设置为与HTTP/HTTPS通信相同的端口，则可以使用以下方法：

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

仅当协议参数为“ftp”时，才使用“http”和“https”选项，并指示指定端口上的隧道是通过HTTPS还是通过HTTP执行。

如果对代理服务器上的FTP/SFTP和HTTP/HTTPS通信使用不同的端口，则应设置“ftp”协议参数。


例如：

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

然后输入密码。

HTTP连接在proxyHTTP参数中定义：

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

HTTPS连接在proxyHTTPS参数中定义：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

FTP/FTPS连接在proxyFTP参数中定义：

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

如果对多种连接类型使用相同的代理，则只定义proxyHTTP并将useSingleProxy设置为“1”或“true”。

如果您有应通过代理的内部连接，请在override参数中添加这些连接。

如果要临时禁用代理连接，请将enabled参数设置为“false”或“0”。
