---
title: 营销活动服务器配置
seo-title: 营销活动服务器配置
description: 营销活动服务器配置
seo-description: null
page-status-flag: never-activated
uuid: a1fadad2-e888-4dd8-bc1f-04df16ba7d46
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: f296676e-3bf1-47da-8239-f5ae54e52fc0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4869eb41f942a89c48bc213913c44b70ae777bfc

---


# 营销活动服务器配置{#campaign-server-configuration}

以下各节详细介绍了必备服务器配置，这些配置将保证Adobe Campaign对大多数设置的有效操作。

配置Campaign服务器中提供 [了其他配置](../../installation/using/configuring-campaign-server.md)。

>[!NOTE]
>
>服务器端配置只能由Adobe为Adobe托管的部署执行。 要进一步了解不同的部署，请参阅托 [管模型部分](../../installation/using/hosting-models.md) ，或本 [文](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)。

## 内部标识符 {#internal-identifier}

内部 **标识符** 是用于安装、管理和维护目的的技术登录名。 此登录名与实例不关联。

使用此登录名连接的运营商将拥有所有实例的所有权限。 如果是新安装，此登录名将没有密码。 必须手动定义此密码。

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

## 配置文件 {#configuration-files}

配置文件存储在Adobe **Campaign安装文件夹** 的conf文件夹中。 配置分布在两个文件上：

* **`config-<instance>.xml`** (其 **中** instance是实例的名称):实例的特定配置。 如果在多个实例之间共享服务器，请在其相关文件中输入每个实例的特定参数。
* **serverConf.xml**:所有实例的常规配置。 此文件结合了Adobe Campaign服务器的技术参数：这些属性由所有实例共享。 下面详细介绍了其中一些参数。 请参阅文件本身以查看所有可用参数。 本节中列出的不同节点和 [参数](../../installation/using/the-server-configuration-file.md)。

您可以配置Adobe Campaign数据(**日志** 、下载、重定向等)的存储目录（var目录）。 为此，请使用 **XTK_VAR_DIR系统变量** :

* 在Windows中，在 **XTK_VAR_DIR系统变量中指示以下值** 。

   ```
   D:\log\AdobeCampaign
   ```

* 在Linux中，转到 **customer.sh文件** ，并指示：导 **出XTK_VAR_DIR=/app/log/AdobeCampaign**。

   For more on this, refer to [Personalizing parameters](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).

## 启用进程 {#enabling-processes}

服务器上的Adobe Campaign进程通过 **config-default.xml和文件启用（和禁用）****`config-<instance>.xml`** 。

要将更改应用于这些文件，如果Adobe Campaign服务已启动，则必须运行 **nlserver config -reload** 命令。

有两种进程：多实例和单实例。

* **多实例**:将为所有实例启动一个进程。 web **、syslogd和** trackinglogd进程 **就是** 这样 **** 。

   可以从 **config-default.xml文件配置Enablement** 。

   声明Adobe Campaign服务器可访问客户端控制台和重定向（跟踪）:

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   在此示例中，使用Linux中的 **vi命令** ，编辑文件。 可以使用任何。txt **或** . **xml编辑器进行编辑** 。

* **单实例**:每个实例(模块：mta、wfserver ******、** Mail **** in **、sms******&#x200B;和stat)。

   可以使用实例的配置文件配置启用：

   ```
   config-<instance>.xml
   ```

   声明服务器用于交付、执行工作流实例和恢复弹回邮件：

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

## 交付设置 {#delivery-settings}

必须在serverConf.xml文件夹中配 **置交付参数** 。

* **DNS配置**:指定从此开始用于响应MTA模块所做MX类型DNS查询的DNS服务器的交付域和IP地址（或主机） **`<dnsconfig>`** 。

   >[!NOTE]
   >
   >nameServers **参数** ，对于在Windows中进行安装是必需的。 对于Linux中的安装，必须将其留空。

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

本文件中提供的其他传送参数在个性化传送 [参数中显示](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)。

另请参阅电子 [邮件交付](../../installation/using/email-deliverability.md)。
