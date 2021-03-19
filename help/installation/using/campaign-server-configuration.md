---
solution: Campaign Classic
product: campaign
title: Campaign 服务器配置
description: Campaign 服务器配置
audience: installation
content-type: reference
topic-tags: initial-configuration
translation-type: tm+mt
source-git-commit: 95d0686c4ddeb4e25eb918ca92cbd6a0b1aa1f3c
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 2%

---


# Campaign 服务器配置{#campaign-server-configuration}

以下部分详细介绍了必备服务器配置，这些配置将保证大多数设置的Adobe Campaign高效运行。

[配置活动服务器](../../installation/using/configuring-campaign-server.md)中提供了其他配置。

>[!NOTE]
>
>服务器端配置只能由Adobe执行，以用于由Adobe托管的部署。 要进一步了解不同的部署，请参阅[托管模型](../../installation/using/hosting-models.md)部分或[功能矩阵](../../installation/using/capability-matrix.md)。

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

## 配置文件{#configuration-files}

配置文件存储在Adobe Campaign安装文件夹的&#x200B;**conf**&#x200B;文件夹中。 配置分布在两个文件上：

* **`config-<instance>.xml`** (其中 **** instance是实例的名称):实例的特定配置。如果您在多个实例之间共享服务器，请在其相关文件中输入每个实例的特定参数。
* **serverConf.xml**:所有实例的常规配置。此文件结合了Adobe Campaign服务器的技术参数：这些属性由所有实例共享。 以下对这些参数的描述详尽。 引用文件本身以视图所有可用参数。 此[节](../../installation/using/the-server-configuration-file.md)中列出的不同节点和参数。

您可以配置存储数据（日志、下载、重定向等）的Adobe Campaign目录（**var**&#x200B;目录）。 为此，请使用&#x200B;**XTK_VAR_DIR**&#x200B;系统变量：

* 在Windows中，在&#x200B;**XTK_VAR_DIR**&#x200B;系统变量中指示以下值

   ```
   D:\log\AdobeCampaign
   ```

* 在Linux中，转到&#x200B;**customer.sh**&#x200B;文件并指示：**导出XTK_VAR_DIR=/app/log/AdobeCampaign**。

   有关详细信息，请参阅[个性化参数](../../installation/using/installing-packages-with-linux.md#personalizing-parameters)。

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

## 投放设置{#delivery-settings}

必须在&#x200B;**serverConf.xml**&#x200B;文件夹中配置投放参数。

* **DNS配置**:指定投放域和DNS服务器的IP地址（或主机），这些DNS服务器用于响应MTA模块从此开始创建的MX类型DNS **`<dnsconfig>`** 查询。

   >[!NOTE]
   >
   >**nameServers**&#x200B;参数对于在Windows中进行安装是必不可少的。 对于Linux中的安装，它必须留空。

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

此文件中提供的其他投放参数显示在[个性化投放参数](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters)中。

另请参阅[电子邮件发送能力](../../installation/using/email-deliverability.md)。
