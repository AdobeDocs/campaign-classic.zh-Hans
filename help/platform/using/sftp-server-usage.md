---
product: campaign
title: SFTP 服务器使用情况
description: 了解有关SFTP服务器最佳实践和疑难解答的更多信息。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d585a5d4-ea33-43c8-aa37-4d892025374a
source-git-commit: 1d32161d60f6b382188012b104c642f504e28645
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 41%

---

# SFTP 服务器最佳实践和故障排除 {#sftp-server-usage}

![](../../assets/common.svg)

## SFTP服务器全局建议 {#global-recommendations}

管理用于 ETL 的文件和数据时，这些文件存储在 Adobe 提供的托管 SFTP 服务器上。使用SFTP服务器时，请确保遵循以下建议。

* 使用基于密钥的身份验证而不是密码身份验证，以避免密码过期（密码的有效期为 90 天）。此外，基于密钥的身份验证允许您生成多个密钥，例如在管理多个实体时。相反，密码身份验证要求您与所管理的所有实体共享密码。

   支持的密钥格式为 SSH-2 RSA 2048。密钥可以使用PyTTY(Windows)或ssh-keygen(Unix)等工具生成。您必须通过向Adobe支持团队提供公共密钥 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 以将其上传到Campaign服务器。

* 在 SFTP 上传和工作流程中使用批处理。

* 处理错误/例外状况。

* 默认情况下，您创建的所有文件夹仅为标识符的读/写模式。创建 Campaign 需要访问的文件夹时，请确保使用整个组的读/写权限进行配置。否则，出于安全原因，工作流程可能无法创建/删除文件，因为它们在同一组内的不同标识符下运行。

* 您尝试启动SFTP连接的公共IP必须添加到Campaign实允许列表例上的。 可通过请求将IP允许列表地址添加到 [Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## 数据库使用最佳实践 {#sftp-server-best-practices}

SFTP服务器设计为临时存储空间，您可以在其上控制文件的保留和删除。

如果未正确使用或监控，这些空间会快速填充服务器上可用的物理空间，并导致文件在后续上载时被截断。 一旦空间饱和，即可触发自动清除并从 SFTP 存储器中删除最旧的文件。

为避免出现此类问题，Adobe建议遵循以下最佳实践。

>[!NOTE]
>
>如果您的实例托管在 AWS 上，则可以使用 Campaign Classic [控制面板](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html)监控 SFTP 服务器存储。要检查您的实例是否托管在 AWS 上，请按照[此页面](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)中详述的步骤操作。
>
>所有管理员用户都可访问控制面板。[此页面](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hans#discover-control-panel)详细介绍了授予用户管理员访问权限的步骤。
>
>请注意，您的实例必须升级为 [最新GA内部版本](../../rn/using/rn-overview.md). 在[本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何确认您的版本。

* 服务器大小容量因许可证而异。在任何情况下，尽量保持最小数据，并且只在需要的时间内保留数据（15 天是最长时间限制）。

* 按照工作流程正确删除数据（通过消费数据的工作流程来管理保留）。

* 时常登入 SFTP 以直接检查其内容。

* 请记住，SFTP 硬盘的管理主要由您负责。

## 外部SFTP服务器使用情况 {#external-SFTP-server}

如果您使用自己的SFTP服务器，请确保尽可能遵循上述建议。

此外，在Campaign Classic指定外部SFTP服务器的路径时，路径语法因SFTP服务器操作系统而异：

* 如果SFTP服务器在 **Windows**，请始终使用相对路径。
* 如果STP服务器在 **Linux**，请始终使用相对于主页的路径（以“~/”开头），或绝对路径（以“/”开头）。

## Adobe托管的SFTP服务器存在连接问题 {#sftp-server-troubleshooting}

以下部分列出了要通过检查并向Adobe支持团队提供的信息 [Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 遇到与Adobe托管的SFTP服务器的连接问题时。

1. 检查您的实例是否正在运行。要执行此操作，请打开您的浏览器，然后 **[!UICONTROL GET]** 在实例中调用 **[!UICONTROL /r/test]** 端点：

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

   如果端口未打开，请确保打开侧面的传出联机，然后重试。如果仍遇到连接问题，请将命令的输出与 [Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 团队。

1. 检查您尝试启动SFTP连接的公共IP是否是您提供给Adobe支持的允许列表IP。
1. 如果您使用基于密码的身份验证，则您的密码可能已过期（密码的有效期为90天）。 因此，我们强烈建议使用基于密钥的身份验证(请参阅 [SFTP服务器最佳实践](#sftp-server-best-practices))。
1. 如果您使用基于密钥的身份验证，请检查您使用的密钥是否与您提供的密钥相同 [Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 用于实例配置的团队。
1. 如果您使用的是 FileZilla 或类似的 FTP 工具，请在支持票证中提供联机日志详细信息。

## “无法解析主机名”错误

此部分提供有关在从Campaign Classic连接到FTP服务器后收到“无法解析主机名”错误时要执行的检查和操作的信息。

工作流日志显示以下日志：

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

尝试从工作流连接FTP服务器并从服务器下载文件时，如果您仍然能够使用FileZilla或WinSCP通过FTP连接，则会出现此错误。

此错误表示无法正确解析FTP服务器域名。 要进行故障诊断，请执行以下操作：

1. 故障诊断 **DNS服务器配置**:

   1. 检查服务器名称是否已添加到本地DNS服务器中。
   1. 如果是，请在Adobe Campaign服务器上运行以下命令以获取IP地址：

      `nslookup <server domain name>`

      这表示FTP服务器正在工作，可从Adobe Campaign应用程序服务器访问该服务器。

1. 故障诊断 **会话日志**:

   1. 在工作流中，双击 [文件传输](../../workflow/using/file-transfer.md) 活动。
   1. 转到 **[!UICONTROL File Transfer]** ，然后单击 **[!UICONTROL Advanced Parameters]**.
   1. 勾选 **[!UICONTROL Display the session logs]** 选项。

      ![](assets/sftp-error-display-logs.png)

   1. 转到工作流审核，并检查日志是否显示“无法解析主机名”错误。

1. 如果SFTP服务器由Adobe托管，请联系客户关怀团队检查是否允许列表已将IP添加到。

   否则，请验证：

   * 密码不包含“@”。 如果密码中存在“@”，则连接失败。
   * 没有防火墙问题会妨碍Adobe Campaign应用程序服务器与SFTP服务器之间的通信。
   * 从Campaign服务器到sftp运行tracert和telnet命令，以查看是否存在任何连接问题。
   * 没有通信协议问题。
   * 端口打开。
