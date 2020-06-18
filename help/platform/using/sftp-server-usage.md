---
title: SFTP 服务器使用情况
seo-title: SFTP 服务器使用情况
description: SFTP 服务器使用情况
seo-description: null
page-status-flag: never-activated
uuid: 5281058d-91bd-4f98-835d-1d46dc7b8b1f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: f449ccd5-3965-4ab8-b5a9-993f3260aba9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fecfff477b0750782c87c017a15e306acac4c61d
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 79%

---


# SFTP 服务器使用情况{#sftp-server-usage}

## SFTP 服务器最佳实践 {#sftp-server-best-practices}

管理用于 ETL 的文件和数据时，这些文件存储在 Adobe 提供的托管 SFTP 服务器上。此 SFTP 旨在作为临时存储空间，您可以在其上控制文件的保留和删除。

如果未正确使用或监视此空间，则此空间可能回快速填满服务器上可用的物理空间，并导致在后续上传时截断文件。一旦空间饱和，即可触发自动清除并从 SFTP 存储器中删除最旧的文件。

为避免出现此类问题，Adobe建议遵循以下最佳实践。

>[!NOTE]
>
>如果您的实例托管在 AWS 上，则可以使用 Campaign Classic [控制面板](https://docs.adobe.com/content/help/en/control-panel/using/sftp-management/sftp-storage-management.html)监控 SFTP 服务器存储。
>
>要检查您的实例是否托管在 AWS 上，请按照[此部分](https://docs.adobe.com/content/help/en/control-panel/using/faq.html#ims-org-id)详述的步骤操作。

* 服务器大小容量因许可证而异。在任何情况下，尽量保持最小数据，并且只在需要的时间内保留数据（15 天是最长时间限制）。
* 使用基于密钥的身份验证而不是密码身份验证，以避免密码过期（密码的有效期为 90 天）。此外，基于密钥的身份验证允许您生成多个密钥，例如在管理多个实体时。相反，密码身份验证要求您与所管理的所有实体共享密码。

   支持的密钥格式为 SSH-2 RSA 2048。密钥可以通过 PuTTY (Windows) 或 ssh-keygen (Unix) 等工具生成。您将必须通过[支持票证](https://support.neolane.net)为 Adobe 支持团队提供公共密钥，将它上传到 Campaign 服务器上。

* 按照工作流程正确删除数据（通过消费数据的工作流程来管理保留）。
* 在 SFTP 上传和工作流程中使用批处理。
* 处理错误/例外状况。
* 时常登入 SFTP 以直接检查其内容。
* 请记住，SFTP 硬盘的管理主要由您负责。
* 默认情况下，您创建的所有文件夹仅为标识符的读/写模式。创建 Campaign 需要访问的文件夹时，请确保使用整个组的读/写权限进行配置。否则，出于安全原因，工作流程可能无法创建/删除文件，因为它们在同一组内的不同标识符下运行。
* 您尝试从中启动SFTP连接的公共IP必须添加到活动实例的允许列表。 可以通过支持票证请求向允许列表添加IP [地址](https://support.neolane.net)。

>[!CAUTION]
>
>如果您使用自己的 SFTP 服务器，请务必尽可能遵循上述建议。

## SFTP 服务器故障排查 {#sftp-server-troubleshooting}

以下部分列出了在遇到与 Adobe 托管的 SFTP 服务器的连接问题时，应通过[支持票证](https://support.neolane.net)检查并提供给 Adobe 支持团队的信息。

1. 检查您的实例是否正在运行。To do this, open your browser, then make a **[!UICONTROL GET]** call on the instance **[!UICONTROL /r/test]** endpoint:

   ```
   https://instanceUrl/r/test
   ```

   如果实例正在运行，您应该得到这种类型的响应：

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instanceName'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instanceName'/>
   ```

   在任何情况下，请在支持票证中提供命令响应。

1. 检查出站端口 22 是否在尝试启动 SFTP 连接的站点上打开。为此，请使用以下命令：

   ```
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   >[!NOTE]
   >
   >Netcat 工具可让您在各种操作系统上轻松管理网络联机（请参见 [https://eternallybored.org/misc/netcat/](https://eternallybored.org/misc/netcat/)）。

   如果端口未打开，请确保打开侧面的传出联机，然后重试。如果仍遇到连接问题，请与 Adobe 支持团队分享该命令的输出。

1. 检查您尝试从中启动SFTP连接的公共IP是否是您提供给Adobe支持部门的允许列表的IP。
1. 如果您使用基于密码的身份验证，则您的密码可能已过期（密码的有效期为90天）。 因此，我们强烈建议使用基于密钥的身份验证(请参 [阅SFTP服务器最佳实践](#sftp-server-best-practices))。
1. 如果您使用的是基于密钥的身份验证，请检查您使用的密钥是否与提供给 Adobe 支持团队以用于实例配置的密钥相同。
1. 如果您使用的是 FileZilla 或类似的 FTP 工具，请在支持票证中提供联机日志详细信息。

