---
solution: Campaign Classic
product: campaign
title: SFTP 服务器使用情况
description: 了解有关SFTP服务器最佳实践和疑难解答的更多信息。
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 564eaedb09282c85593f638617baded0a63494a0
workflow-type: tm+mt
source-wordcount: '1158'
ht-degree: 33%

---


# SFTP 服务器最佳实践和疑难解答 {#sftp-server-usage}

## SFTP服务器全局推荐{#global-recommendations}

管理用于 ETL 的文件和数据时，这些文件存储在 Adobe 提供的托管 SFTP 服务器上。确保在使用SFTP服务器时遵循以下建议。

* 使用基于密钥的身份验证而不是密码身份验证，以避免密码过期（密码的有效期为 90 天）。此外，基于密钥的身份验证允许您生成多个密钥，例如在管理多个实体时。相反，密码身份验证要求您与所管理的所有实体共享密码。

   支持的密钥格式为 SSH-2 RSA 2048。可以使用PyTTY(Windows)或ssh-keygen(Unix)等工具生成密钥。您必须通过[Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)将公钥提供给活动支持团队，才能将其上传到Adobe服务器上。

* 在 SFTP 上传和工作流程中使用批处理。

* 处理错误/例外状况。

* 默认情况下，您创建的所有文件夹仅为标识符的读/写模式。创建 Campaign 需要访问的文件夹时，请确保使用整个组的读/写权限进行配置。否则，出于安全原因，工作流程可能无法创建/删除文件，因为它们在同一组内的不同标识符下运行。

* 您尝试从中启动SFTP连接的公用IP必须添加到实允许列表例上的活动。 可以通过[允许列表Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)请求向添加IP地址。

## 数据库使用最佳实践{#sftp-server-best-practices}

SFTP服务器设计为临时存储空间，您可以控制文件的保留和删除。

当使用或监视不正确时，这些空间可以快速填充服务器上可用的物理空间，并导致文件在后续上载时被截断。 一旦空间饱和，即可触发自动清除并从 SFTP 存储器中删除最旧的文件。

为避免出现此类问题，Adobe建议遵循以下最佳做法。

>[!NOTE]
>
>如果您的实例托管在 AWS 上，则可以使用 Campaign Classic [控制面板](https://docs.adobe.com/content/help/en/control-panel/using/sftp-management/sftp-storage-management.html)监控 SFTP 服务器存储。要检查您的实例是否托管在AWS上，请按照[本页](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)中详细介绍的步骤操作。
>
>控制面板可供所有管理员用户访问。 授予用户管理员访问权限的步骤详见[此页](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel)。
>
>请注意，您的实例必须使用最新的[金标](../../rn/using/gs-overview.md)版本或最新的[ GA内部版本(21.1)](../../rn/using/latest-release.md)进行升级。 了解如何在[本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中检查您的版本。

* 服务器大小容量因许可证而异。在任何情况下，尽量保持最小数据，并且只在需要的时间内保留数据（15 天是最长时间限制）。

* 按照工作流程正确删除数据（通过消费数据的工作流程来管理保留）。

* 时常登入 SFTP 以直接检查其内容。

* 请记住，SFTP 硬盘的管理主要由您负责。

## 外部SFTP服务器使用{#external-SFTP-server}

如果您使用自己的SFTP服务器，请确保尽可能遵循上述建议。

此外，在Campaign Classic指定到外部SFTP服务器的路径时，路径语法根据SFTP服务器操作系统而有所不同：

* 如果SFTP服务器位于&#x200B;**Windows**&#x200B;上，请始终使用相对路径。
* 如果STP服务器位于&#x200B;**Linux**&#x200B;上，请始终使用相对于主页的路径（以&quot;~/&quot;开头）或绝对路径（以&quot;/&quot;开头）。

## Adobe托管SFTP服务器{#sftp-server-troubleshooting}的连接问题

下面的部分将列表信息，以便在遇到与Adobe托管的SFTP服务器的连接问题时，通过[Adobe客户关怀](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)向Adobe支持团队提供信息。

1. 检查您的实例是否正在运行。为此，请打开浏览器，然后对实例&#x200B;**[!UICONTROL /r/test]**&#x200B;端点进行&#x200B;**[!UICONTROL GET]**&#x200B;调用：

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

   如果端口未打开，请确保打开侧面的传出联机，然后重试。如果仍遇到连接问题，请与[Adobe客户关怀团队共享命令输出。](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)

1. 检查您试图从中启动SFTP连接的公共IP是否是您提供给Adobe支持的允许列表IP。
1. 如果您使用基于密码的身份验证，则您的密码可能已过期（密码的有效期为90天）。 因此，我们强烈建议使用基于密钥的身份验证（请参阅[SFTP服务器最佳实践](#sftp-server-best-practices)）。
1. 如果您使用基于密钥的身份验证，请检查您使用的密钥是否与您为实例配置向[Adobe客户关怀团队提供的密钥相同。](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)
1. 如果您使用的是 FileZilla 或类似的 FTP 工具，请在支持票证中提供联机日志详细信息。

## &quot;无法解析主机名&quot;错误

本节提供在从Campaign Classic连接到FTP服务器后收到“无法解析主机名”错误时要执行的检查和操作的信息。

工作流日志显示以下日志：

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

当您尝试从工作流连接FTP服务器并从服务器下载文件时，此错误会发生，而您仍能使用FileZilla或WinSCP通过FTP连接。

此错误表示无法正确解析FTP服务器域名。 要进行疑难解答，请执行以下操作：

1. **DNS服务器配置**&#x200B;疑难解答：

   1. 检查是否已将服务器名称添加到本地DNS服务器。
   1. 如果是，请在Adobe Campaign服务器上运行以下命令以获取IP地址：

      `nslookup <server domain name>`

      这将确认FTP服务器正在工作，并可从Adobe Campaign应用程序服务器访问。

1. **会话日志**&#x200B;疑难解答：

   1. 在工作流中，多次单击[文件传输](../../workflow/using/file-transfer.md)活动。
   1. 转到&#x200B;**[!UICONTROL File Transfer]**&#x200B;选项卡，然后单击&#x200B;**[!UICONTROL Advanced Parameters]**。
   1. 勾选 **[!UICONTROL Display the session logs]** 选项。

      ![](assets/sftp-error-display-logs.png)

   1. 转到工作流审核并检查日志是否显示“无法解析主机名”错误。

1. 如果SFTP服务器由Adobe托管，请联系客户关怀部门，检查是否将IP允许列表添加到中。

   否则验证：

   * 密码不包含“@”。 如果密码中存在“@”，则连接失败。
   * 没有防火墙问题会妨碍Adobe Campaign应用程序服务器与SFTP服务器之间的通信。
   * 从活动服务器到sftp运行tracert和telnet命令，查看是否存在连接问题。
   * 没有通信协议问题。
   * 端口已打开。
