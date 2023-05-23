---
product: campaign
title: 监测准则
description: 了解监控 Campaign 实例和流程的准则和最佳实践
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Monitoring
exl-id: ca0c33c5-7350-462a-bc65-4cab51e529d9
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 21%

---

# 监测准则 {#monitoring-guidelines}



## 執行個體監視儀表板 {#instance-monitoring-dashboard}

此 **[!UICONTROL Monitoring]** tab (可從Campaign Classic首頁存取)是協助您監視執行個體的主要進入點。

它提供執行個體上所發生情況的儀表板：其狀態（組建版本、已安裝套件等）、系統指標、記錄、目前正在執行的工作流程、上次傳送傳遞的狀態等。

详情请见[此处](../../production/using/monitoring-processes.md)。

![](assets/monitoring_tab.png)

## 監視Campaign Classic程式 {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">監視您的執行個體</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#monitoring-workflows">监测工作流</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">监测投放</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">監視資料庫</a></p></td></tr>
</table>

有其他方法可監控不同的Campaign流程。 它們提供數種監視執行個體的方式，以確保您的系統狀況良好，並最終疑難排解設定工作流程、傳送傳遞等時可能發生的問題。

### 監視執行個體 {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**自動監控工具**

有數種自動方法可供使用。 協助您監控執行個體。 例如，您可以設定包含偵測到異常的電子郵件報表、擷取XML格式的指標清單等。 [单击此处](../../production/using/monitoring-processes.md#automatic-monitoring)以了解更多信息。

**审核跟踪**

稽核軌跡可讓您以視覺效果呈現執行個體中與選項、工作流程及結構描述相關的變更完整歷史記錄。 [单击此处](../../production/using/audit-trail.md)以了解更多信息。

**控制面板**

「控制面板」可讓您管理執行個體的多項設定：管理URL許可權、檢查執行個體詳細資訊（例如伺服器的組建版本）等。 它也可讓您監視連線到執行個體的SFTP伺服器上的可用空間。 [单击此处](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hans)以了解更多信息。

>[!NOTE]
>
>所有管理员用户都可访问控制面板。[此页面](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hans#discover-control-panel)详细介绍了授予用户管理员访问权限的步骤。
>
>請注意，您的執行個體必須託管於AWS上，並透過以下方式升級： [最新GA版本編號](../../rn/using/rn-overview.md). 在[本节](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何确认您的版本。要检查您的实例是否托管在 AWS 上，请按照[此页面](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)中详述的步骤操作。

### 监控工作流 {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**工作流热图**

工作流程熱度圖提供執行個體上執行之所有工作流程的視覺化表示。 它可讓您輕鬆監控執行個體的負載，並據此規劃工作流程。 [单击此处](../../workflow/using/heatmap.md)以了解更多信息。

**审核跟踪**

稽核軌跡可讓您以視覺效果呈現工作流程中所做的所有修改及其目前狀態。 [单击此处](../../production/using/audit-trail.md).

**工作流程疑難排解**

遇到工作流程執行問題時，可執行特定動作。 [按一下這裡](../../production/using/workflow-execution.md) 以取得詳細資訊

**工作流程狀態監視**

除了熱度圖之外，您還可以建立工作流程，讓您監視一組工作流程的狀態，並傳送週期性訊息給主管。 [单击此处](../../workflow/using/supervising-workflows.md)以了解更多信息。

**一般准則**

使用工作流程時，遵循准則和最佳實務有助於改善效能。 如需詳細資訊，請參閱下列章節：
* [使用工作流程時的最佳實務](../../workflow/using/workflow-best-practices.md)
* [监控工作流执行](../../workflow/using/monitoring-workflow-execution.md)

### 监控投放 {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP報表**

SMTP報告會依網域顯示傳遞統計資料和SMTP錯誤。 [了解详情](../../production/using/monitoring-processes.md)

**最佳做法**

[傳遞傳送和設計的最佳實務](../../delivery/using/delivery-best-practices.md) 可協助您改善其效能。

**傳遞疑難排解**
遇到傳送問題時，可執行特定動作：
* [傳遞能力問題](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [图像显示问题](../../production/using/image-display-issues.md)
* [傳遞效能問題](../../delivery/using/delivery-performances.md)
* [暫存檔問題](../../production/using/temporary-files.md) - *僅限內部部署託管模型*

### 監視資料庫 {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**数据库清理工作流**

資料庫清理工作流程可讓您從資料庫中刪除過時的資料。 建議避免資料庫呈指數增長。 [单击此处](../../production/using/database-cleanup-workflow.md)以了解更多信息。

**資料庫效能疑難排解**

遇到資料庫效能問題時，可執行特定動作。 [单击此处](../../production/using/database-performances.md)以了解更多信息。

**数据库维护**

*僅限內部部署和混合託管模型*

建議您定期執行資料庫維護，以避免過度消耗磁碟空間，進而影響資料庫存取。 [单击此处](../../production/using/recommendations.md)以了解更多信息。

**備份與還原**

*僅限內部部署和混合託管模型*

備份是必要的，以避免在電腦上發生問題（無論是實體或系統相關問題）時遺失資料。 [单击此处](../../production/using/backup.md)以了解更多信息。復原程式的說明，請參閱 [本節](../../production/using/restoration.md).

## Campaign Classic技術原則 {#campaign-classic-technical-principles}

技術資源可在Campaign Classic檔案中取得。 在執行個體上執行任何技術操作之前，建議您先熟悉這些主題。

**託管模型與功能**

* [Campaign Classic託管模型](../../installation/using/hosting-models.md)
* [託管模型功能](../../installation/using/capability-matrix.md)

**服务器配置**

*僅限內部部署和混合託管模型*

* [伺服器設定](../../installation/using/configuring-campaign-server.md)
* [Serverconf.xml檔案設定](../../installation/using/the-server-configuration-file.md)
* [傳遞能力的伺服器設定](../../installation/using/email-deliverability.md)
* [建立執行個體和宣告資料庫的命令列](../../installation/using/command-lines.md)

**一般原則**

* [Campaign Classic架構](../../production/using/general-architecture.md)
* [Campaign Classic模組](../../production/using/operating-principle.md)
* [Campaign Classic選項](../../installation/using/configuring-campaign-options.md)
* [如何設定模組的自動啟動](../../production/using/administration.md)
* [Campaign設定原則](../../production/using/configuration-principle.md)
* [疑難排解程式](../../production/using/performance-and-throughput-issues.md)
