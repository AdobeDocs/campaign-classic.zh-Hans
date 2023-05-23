---
product: campaign
title: SFTP 服务器使用情况
description: 深入瞭解SFTP伺服器最佳實務和疑難排解
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d585a5d4-ea33-43c8-aa37-4d892025374a
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 41%

---

# SFTP 服务器最佳实践和故障排除 {#sftp-server-usage}



## SFTP伺服器全域建議 {#global-recommendations}

管理用于 ETL 的文件和数据时，这些文件存储在 Adobe 提供的托管 SFTP 服务器上。使用SFTP伺服器時，請務必遵循下列建議。

* 使用基于密钥的身份验证而不是密码身份验证，以避免密码过期（密码的有效期为 90 天）。此外，基于密钥的身份验证允许您生成多个密钥，例如在管理多个实体时。相反，密码身份验证要求您与所管理的所有实体共享密码。

   支持的密钥格式为 SSH-2 RSA 2048。金鑰可由PyTTY (Windows)或ssh-keygen (Unix)等工具產生。您必須透過以下方式向Adobe支援團隊提供公開金鑰： [Adobe客戶服務](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 將其上傳至Campaign伺服器。

* 在 SFTP 上传和工作流程中使用批处理。

* 处理错误/例外状况。

* 默认情况下，您创建的所有文件夹仅为标识符的读/写模式。创建 Campaign 需要访问的文件夹时，请确保使用整个组的读/写权限进行配置。否则，出于安全原因，工作流程可能无法创建/删除文件，因为它们在同一组内的不同标识符下运行。

* 您嘗試啟動SFTP連線的公用IP必須新增至Campaign執行個體上的允許清單。 可透過以下方式請求將IP位址新增至允許清單 [Adobe客戶服務](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## 資料庫使用最佳實務 {#sftp-server-best-practices}

SFTP伺服器是專為臨時儲存空間而設計，您可以在其上控制檔案的保留和刪除。

若未正確使用或監控，這些空間會快速填滿伺服器上可用的實體空間，並導致檔案在後續上傳時被截斷。 一旦空间饱和，即可触发自动清除并从 SFTP 存储器中删除最旧的文件。

為避免此類問題，Adobe建議遵循以下最佳實務。

>[!NOTE]
>
>如果您的实例托管在 AWS 上，则可以使用 Campaign Classic [控制面板](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html)监控 SFTP 服务器存储。要检查您的实例是否托管在 AWS 上，请按照[此页面](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)中详述的步骤操作。
>
>所有管理员用户都可访问控制面板。[此页面](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hans#discover-control-panel)详细介绍了授予用户管理员访问权限的步骤。
>
>請注意，您的執行個體必須升級為 [最新GA版本編號](../../rn/using/rn-overview.md). 在[本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何确认您的版本。

* 服务器大小容量因许可证而异。在任何情况下，尽量保持最小数据，并且只在需要的时间内保留数据（15 天是最长时间限制）。

* 按照工作流程正确删除数据（通过消费数据的工作流程来管理保留）。

* 时常登入 SFTP 以直接检查其内容。

* 请记住，SFTP 硬盘的管理主要由您负责。

## 外部SFTP伺服器使用情況 {#external-SFTP-server}

如果您使用自己的SFTP伺服器，請務必儘可能遵循上述建議。

此外，在Campaign Classic中指定外部SFTP伺服器的路徑時，路徑語法會因SFTP伺服器作業系統而異：

* 如果您的SFTP伺服器為 **Windows**，請一律使用相對路徑。
* 如果您的STP伺服器已開啟 **Linux**，請一律使用與首頁相關的路徑（以「~/」開頭）或絕對路徑（以「/」開頭）。

## Adobe代管SFTP伺服器的連線問題 {#sftp-server-troubleshooting}

以下區段列出要檢查的資訊，並透過提供給Adobe支援團隊 [Adobe客戶服務](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 遇到Adobe代管SFTP伺服器的連線問題時。

1. 检查您的实例是否正在运行。若要這麼做，請開啟瀏覽器，然後建立 **[!UICONTROL GET]** 在執行個體上呼叫 **[!UICONTROL /r/test]** 端點：

   ```
   https://instanceUrl/r/test
   ```

   如果实例正在运行，您应该得到这种类型的响应：

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instance-name'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instance-name'/>
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

   如果端口未打开，请确保打开侧面的传出联机，然后重试。如果您仍然遇到連線問題，請將命令的輸出分享給 [Adobe客戶服務](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 團隊。

1. 檢查您嘗試啟動SFTP連線的公用IP是否為您提供給允許清單Adobe支援的IP。
1. 如果您使用以密碼為基礎的驗證，您的密碼可能已過期（密碼的有效期為90天）。 因此，我們強烈建議使用金鑰式驗證(請參閱 [SFTP伺服器最佳實務](#sftp-server-best-practices))。
1. 如果您使用以金鑰為基礎的驗證，請檢查您使用的金鑰是否與您提供給的金鑰相同 [Adobe客戶服務](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 執行個體組態的團隊。
1. 如果您使用的是 FileZilla 或类似的 FTP 工具，请在支持票证中提供联机日志详细信息。

## 「無法解析主機名稱」錯誤

本節提供從Campaign Classic連線至FTP伺服器後收到「無法解析主機名稱」錯誤時，所要執行的檢查和動作的相關資訊。

工作流程日誌會顯示以下記錄：

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

嘗試從工作流程連線FTP伺服器並從伺服器下載檔案時，當您仍可使用FileZilla或WinSCP透過FTP連線時，就會發生此錯誤。

此錯誤表示無法正確解析FTP伺服器網域名稱。 若要進行疑難排解，請執行下列動作：

1. 疑難排解 **DNS伺服器設定**：

   1. 檢查伺服器名稱是否已新增至本機DNS伺服器。
   1. 如果是，請在Adobe Campaign伺服器上執行下列命令以取得IP位址：

      `nslookup <server domain name>`

      這可確認FTP伺服器是否正常運作，以及是否可從Adobe Campaign應用程式伺服器連線。

1. 疑難排解 **工作階段記錄**：

   1. 在工作流程中，按兩下 [檔案傳輸](../../workflow/using/file-transfer.md) 活動。
   1. 前往 **[!UICONTROL File Transfer]** 標籤，然後按一下 **[!UICONTROL Advanced Parameters]**.
   1. 勾选 **[!UICONTROL Display the session logs]** 选项。

      ![](assets/sftp-error-display-logs.png)

   1. 前往工作流程稽核，並檢查記錄是否顯示「無法解析主機名稱」錯誤。

1. 如果SFTP伺服器是由Adobe託管，請聯絡客戶服務，檢查是否將IP新增至允許清單。

   否則，請驗證：

   * 密碼不包含&#39;@&#39;。 如果密碼中有&#39;@&#39;，連線就會失敗。
   * 沒有防火牆問題會妨礙Adobe Campaign應用程式伺服器與SFTP伺服器之間的通訊。
   * 從campaign伺服器執行tracert和telnet命令至sftp，檢視是否有任何連線問題。
   * 沒有通訊協定問題。
   * 連線埠已開啟。
