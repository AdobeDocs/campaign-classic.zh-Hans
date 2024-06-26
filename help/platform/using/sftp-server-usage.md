---
product: campaign
title: SFTP 服务器使用情况
description: 了解有关SFTP服务器最佳实践和故障排除的更多信息
feature: Troubleshooting
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d585a5d4-ea33-43c8-aa37-4d892025374a
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 24%

---

# SFTP 服务器最佳实践和故障排除 {#sftp-server-usage}



## SFTP服务器全局推荐 {#global-recommendations}

管理用于 ETL 的文件和数据时，这些文件存储在 Adobe 提供的托管 SFTP 服务器上。使用SFTP服务器时，请确保遵循以下建议。

* 使用基于密钥的身份验证而不是密码身份验证，以避免密码过期（密码的有效期为90天）。 此外，基于密钥的身份验证允许您生成多个密钥，例如在管理多个实体时。 相反，密码身份验证要求您与所管理的所有实体共享密码。

  支持的密钥格式为SSH-2 RSA 2048。 密钥可以使用PyTTY (Windows)或ssh-keygen (Unix)等工具生成。您必须通过向Adobe支持团队提供公共密钥 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 以将其上传到Campaign服务器。

* 在 SFTP 上传和工作流程中使用批处理。

* 处理错误/例外状况。

* 默认情况下，您创建的所有文件夹仅针对您的标识符处于读/写模式。 创建需要Campaign访问的文件夹时，请确保使用整个组的读/写权限对其进行配置。 否则，出于安全原因，工作流程可能无法创建/删除文件，因为它们在同一组内的不同标识符下运行。

* 列入允许列表您尝试启动SFTP连接的公共IP必须添加到Campaign实例的中。 可以通过向允许列表添加IP地址 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## 数据库使用最佳实践 {#sftp-server-best-practices}

SFTP服务器旨在作为临时存储空间，您可以在其上控制文件的保留和删除。

如果未正确使用或监控，这些空间会快速填充服务器上可用的物理空间，并导致文件在后续上传时被截断。 一旦空间饱和，即可触发自动清除并从 SFTP 存储器中删除最旧的文件。

为避免此类问题，Adobe建议遵循以下最佳实践。

>[!NOTE]
>
>如果您的实例托管在AWS上，则可以使用Campaign Classic监控SFTP服务器的存储空间 [控制面板](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html). 要检查您的实例是否托管在 AWS 上，请按照[此页面](https://experienceleague.adobe.com/docs/control-panel/using/faq.html?lang=zh-Hans)中详述的步骤操作。
>
>所有管理员用户都可访问控制面板。[此页面](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hans#discover-control-panel)详细介绍了授予用户管理员访问权限的步骤。
>
>请注意，您的实例必须使用 [最新GA版本](../../rn/using/rn-overview.md). 了解如何在中签入您的版本 [本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

* 服务器大小功能因您的许可证而异。 在任何情况下，尽量保持最小数据，并且只在需要的时间内保留数据（15 天是最长时间限制）。

* 按照工作流程正确删除数据（通过消费数据的工作流程来管理保留）。

* 时常登入 SFTP 以直接检查其内容。

* 请记住，SFTP 硬盘的管理主要由您负责。

## 外部SFTP服务器使用情况 {#external-SFTP-server}

如果您使用自己的SFTP服务器，请确保尽可能多地遵循上述建议。

此外，在Campaign Classic中指定外部SFTP服务器的路径时，路径语法因SFTP服务器操作系统而异：

* 如果您的SFTP服务器为 **Windows**，始终使用相对路径。
* 如果您的STP服务器为 **Linux**，请始终使用相对于主目录的路径（以“~/”开头）或绝对路径（以“/”开头）。

## Adobe托管的SFTP服务器的连接问题 {#sftp-server-troubleshooting}

以下部分列出了要检查的信息，并通过提供给Adobe支持团队 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) Adobe托管的SFTP服务器遇到连接问题时。

1. 检查您的实例是否正在运行。 为此，请打开浏览器，然后制作 **[!UICONTROL GET]** 在实例上调用 **[!UICONTROL /r/test]** 端点：

   ```
   https://instanceUrl/r/test
   ```

   如果实例正在运行，您应该得到这种类型的响应：

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instance-name'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instance-name'/>
   ```

   在任何情况下，请在支持票证中提供命令响应。

1. 检查在尝试启动SFTP连接的站点上是否打开了出站端口22。 为此，请使用以下命令：

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

   如果未打开端口，请确保在侧打开出站连接，然后重试。 如果您仍然遇到连接问题，请将命令输出共享给 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 团队。

1. 检查您尝试启动SFTP连接的公共IP是否就是您向Adobe支持部门提供的IP，以便进行SFTP列入允许列表。
1. 如果使用基于密码的身份验证，则密码可能已过期（密码的有效期为90天）。 因此，我们强烈建议使用基于密钥的身份验证(请参阅 [SFTP服务器最佳实践](#sftp-server-best-practices))。
1. 如果您使用基于密钥的身份验证，请检查您使用的密钥是否与提供给的密钥相同 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 组成实例配置的团队。
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

当尝试从工作流连接FTP服务器并从服务器下载文件时，当您仍然可以使用FileZilla或WinSCP通过FTP连接时，会发生此错误。

此错误表示无法正确解析FTP服务器域名。 要进行故障诊断，请执行以下操作：

1. 疑难解答 **DNS服务器配置**：

   1. 检查服务器名称是否已添加到本地DNS服务器。
   1. 如果是，请在Adobe Campaign服务器上运行以下命令以获取IP地址：

      `nslookup <server domain name>`

      这可以确认FTP服务器是否工作以及是否可从Adobe Campaign应用程序服务器访问。

1. 疑难解答 **会话日志**：

   1. 在工作流中，双击 [文件传输](../../workflow/using/file-transfer.md) 活动。
   1. 转到 **[!UICONTROL File Transfer]** 选项卡，然后单击 **[!UICONTROL Advanced Parameters]**.
   1. 勾选 **[!UICONTROL Display the session logs]** 选项。

      ![](assets/sftp-error-display-logs.png)

   1. 转到工作流审核并检查日志是否显示“无法解析主机名”错误。

1. 如果SFTP服务器由Adobe列入允许列表托管，请联系客户关怀部门以检查IP是否已添加到。

   否则，请验证：

   * 密码不包含“@”。 如果密码中存在“@”，则连接失败。
   * 没有防火墙问题会阻碍Adobe Campaign应用程序服务器与SFTP服务器之间的通信。
   * 从campaign服务器向sftp运行tracert和telnet命令，以查看是否存在任何连接问题。
   * 不存在通信协议问题。
   * 端口已打开。
