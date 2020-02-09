---
title: CRM连接器
seo-title: CRM连接器
description: CRM连接器
seo-description: null
page-status-flag: never-activated
uuid: ef3d88a1-b0fd-4790-b6e8-63fa339ef991
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dbe9080c-66e3-4ff6-8f16-959f9748f666
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# CRM连接器{#crm-connectors}

## 关于CRM连接器 {#about-crm-connectors}

Adobe Campaign 提供各种 CRM 连接器，可将您的 Adobe Campaign 平台链接到第三方系统。通过这些 CRM 连接器，您可以同步处理联系人、帐户、购买等。您可以使用这些 CRM 连接器轻松地将您的应用程序与各第三方和商务应用程序相集成。

通过这些连接器，可快速轻松地集成数据：Adobe Campaign 提供专用的向导，让您从 CRM 中提供的表中收集和选择数据。并且可确保双向同步处理，让整个系统中的数据随时保持最新。

>[!NOTE]
>
>通过 **CRM连接器专用包，Adobe Campaign中提供此功** 能。

通过专用的工作流活动连接到CRM。 本节介绍的章节详细介绍了这些 [活动](../../workflow/using/crm-connector.md)。

### 兼容的CRM系统和限制 {#compatible-crm-systems-and-limitations}

下面列出的CRM可集成到Adobe Campaign中。

兼容性列表中详细介绍了支 [持的版本](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

* **Salesforce.com**

   请参阅 [此部分](#example-for-salesforce-com) ，了解如何设置与Salesforce.com的连接。

   >[!CAUTION]
   >
   >将Adobe Campaign与Salesforce.com连接时，限制如下：
   >
   >    
   >    
   >    * 支持测试生产实例。
   >    * 支持分配规则。
   >    * Adobe Campaign不支持多个选择枚举。


* **Oracle On Demand**

   请参阅 [本节](#example-for-oracle-on-demand) ，了解如何设置与Oracle On Demand的连接。

   >[!CAUTION]
   >
   >在将Adobe Campaign与Oracle On Demand连接时，限制如下：
   >
   >    
   >    
   >    * Adobe Campaign可以同步标准Oracle On Demand模板中可用的任何对象。 如果您已在Oracle On Demand中添加了个性化表，则这些表将无法在Adobe Campaign中恢复。
   >    * API版本1.0允许您在查询过程中对数据进行排序或过滤，但不允许同时执行这两项操作。
   >    * Oracle On Demand发送的日期不包含时区信息。
   >    * Adobe Campaign不支持多个选择枚举。


* **MS Dynamics CRM** and **MS Dynamics Online**

   请参 [阅本节](#example-for-microsoft-dynamics) ，了解如何设置与Microsoft Dynamics的连接。

   在此视频中了解Adobe Campaign和Microsoft Dynamics的集成用 [例](https://helpx.adobe.com/campaign/kt/acc/using/acc-integrate-dynamics365-with-acc-feature-video-set-up.html)。

   >[!CAUTION]
   >
   >将Adobe Campaign与Microsoft Dynamics连接时，限制如下：
   >
   >    
   >    
   >    * 安装插件可以更改CRM的行为，这会导致与Adobe Campaign的兼容性问题。
   >    * Adobe Campaign不支持多个选择枚举。


## 设置连接 {#setting-up-the-connection}

要在Adobe Campaign中使用CRM连接器，请应用以下步骤：

1. 创建外部帐户
1. 收集CRM表
1. 同步枚举
1. 创建同步工作流

>[!NOTE]
>
>CRM连接器只能使用安全URL(https)。

### Salesforce.com示例 {#example-for-salesforce-com}

要配置 **Salesforce.com连接器与Adobe Campaign** ，请执行以下步骤：

1. 通过Adobe Campaign树的节点 **[!UICONTROL Administration > Platform > External accounts]** 创建新的外部帐户。
1. 运行配置向导以生成可用的CRM表。

   ![](assets/crm_connectors_sfdc_wz.png)

   通过配置向导，您可以收集表并创建匹配的架构。

   单击 **[!UICONTROL Start]** 以运行执行。

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >要批准设置，您需要注销并重新登录到Adobe Campaign控制台。

1. 检查在节点的Adobe Campaign中生成的架 **[!UICONTROL Administration > Configuration > Data schemas]** 构。

   ![](assets/crm_connectors_sfdc_table.png)

1. 创建架构后，您可以通过CRM自动将枚举同步到Adobe Campaign。

   为此，请单击链接， **[!UICONTROL Synchronizing enumerations...]** 然后选择与CRM枚举相匹配的Adobe Campaign枚举。

   您可以将Adobe Campaign枚举的所有值替换为CRM的值：为此，请在列 **[!UICONTROL Yes]** 中选 **[!UICONTROL Replace]** 择。

   ![](assets/crm_connectors_sfdc_enum.png)

   单 **[!UICONTROL Next]** 击，然 **[!UICONTROL Start]** 后开始导入列表。

1. 检查菜单中导入的 **[!UICONTROL Administration > Platform > Enumerations]** 值。

   ![](assets/crm_connectors_sfdc_exe.png)

1. 要导入Salesforce数据或将Adobe Campaign数据导出到Salesforce，您需要创建工作流并使用活 **[!UICONTROL CRM connector]** 动。

   ![](assets/crm_connectors_sfdc_wf.png)

### Oracle On Demand示例 {#example-for-oracle-on-demand}

要将 **Oracle On Demand** Connector配置为与Adobe Campaign一起使用，请应用以下步骤：

1. 通过Adobe Campaign树的节点 **[!UICONTROL Administration > Platform > External accounts]** 创建新的外部帐户。

   ![](assets/crm_connectors_ood_1.png)

1. 打开配置向导：Adobe Campaign会自动显示Oracle数据模型的表。 选择要收集的表。

   ![](assets/crm_connectors_ood_2.png)

1. 单击 **[!UICONTROL Next]** 以开始创建匹配的架构。

   Adobe Campaign中将提供匹配的数据架构。

   ![](assets/crm_connectors_ood_3.png)

1. 开始在Adobe Campaign和Oracle On Demand之间同步枚举。

   ![](assets/crm_connectors_ood_4.png)

1. 要将Oracle On Demand数据导入Adobe Campaign，请创建以下类型的工作流：

   ![](assets/crm_connectors_ood_5.png)

   此工作流通过Oracle On Demand导入联系人，将其与现有Adobe Campaign数据同步，删除重复的联系人，并更新Adobe Campaign数据库。

   活 **[!UICONTROL CRM Connector]** 动需要进行配置，如下所示：

   ![](assets/crm_connectors_ood_6.png)

1. 要将Adobe Campaign数据导出到Oracle On Demand，请创建以下工作流：

   ![](assets/crm_connectors_ood_7.png)

   此工作流使用查询收集相关数据，然后将其导出到Oracle On Demand联系人表中。

### Microsoft Dynamics的示例 {#example-for-microsoft-dynamics}

要配置Microsoft Dynamics连接器以与Adobe Campaign结合使用，请应用以下步骤：

1. 通过Adobe Campaign树的节点 **[!UICONTROL Administration > Platform > External accounts]** 创建新的外部帐户。

   ![](assets/crm_connectors_msdynamics_01_4.png)

1. 选择部 **署类型**:或 **[!UICONTROL On-premise]**&#x200B;者 **[!UICONTROL Office 365]****[!UICONTROL Web API]**，具体取决于要配置的连接器。

   Adobe Campaign Classic支持Dynamics 365 REST接口和OAuth协议，用于身份验证。

   如果选择部 **[!UICONTROL WebAPI]** 署，则需要在Azure目录上注册应用程序并从Azure目录 **获取clientId** 。 本页介绍了此 [注册](https://msdn.microsoft.com/en-us/library/mt622431.aspx)。

   >[!NOTE]
   >
   >Adobe Campaign Classic不需要redirectURL参数。

   clientId **值与用户名** /密码一起使用，以使用授予类型密码获取承载令牌。 这称为“资 **源所有者密码凭据授权”**。 有关详细信息，请参见[此页面](https://blogs.msdn.microsoft.com/wushuai/2016/09/25/resource-owner-password-credentials-grant-in-azure-ad-oauth/)。

   ![](assets/crm_connectors_msdynamics_01_3.png)

   有关CRM版本兼容性的详细信息，请参阅兼容性 [表](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

1. 打开配置向导。 Adobe Campaign会从Microsoft Dynamics数据模板自动检测表。

   ![](assets/crm_connectors_msdynamics_02.png)

   选择要恢复的表。

   ![](assets/crm_connectors_msdynamics_03.png)

1. 单击 **[!UICONTROL Next]** 并开始创建相应的架构。

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >要批准该配置，您必须断开／重新连接到Adobe Campaign控制台。

   Adobe Campaign中将提供匹配的数据架构。

   ![](assets/crm_connectors_msdynamics_05.png)

1. 开始在Adobe Campaign和Microsoft dynamics之间同步枚举。

   ![](assets/crm_connectors_msdynamics_06.png)

1. 要将Microsoft Dynamics数据导入Adobe Campaign，请创建以下类型的工作流：

   ![](assets/crm_connectors_msdynamics_07.png)

   此工作流通过Microsoft Dynamics导入联系人，将其与现有Adobe Campaign数据同步，删除重复的联系人，并更新Adobe Campaign数据库。

   活 **[!UICONTROL CRM Connector]** 动需要配置如下：

   ![](assets/crm_connectors_msdynamics_08.png)

## 数据同步 {#data-synchronization}

Adobe Campaign和CRM之间的同步是通过专用的工作流活动进行的： [CRM连接器](../../workflow/using/crm-connector.md)。

通过此活动，您可以：

* 从CRM导入(请参阅 [从CRM导入](#importing-from-the-crm)),
* 导出到CRM(请参 [阅导出到CRM](#exporting-to-the-crm)),
* 导入在CRM中删除的对象(请参阅 [在CRM中删除的导入对象](#importing-objects-deleted-in-the-crm)),
* 在CRM中删除对象(请参阅 [在CRM中删除对象](#deleting-objects-in-the-crm))。

![](assets/crm_task_select_op.png)

选择与要配置同步的CRM匹配的外部帐户，然后选择要同步的对象（帐户、业务机会、潜在客户、联系人等）。

![](assets/crm_task_select_obj.png)

此活动的配置取决于要执行的过程。 以下详细介绍了各种配置。

### 从CRM导入 {#importing-from-the-crm}

要在Adobe Campaign中通过CRM导入数据，您需要创建以下类型的工作流：

![](assets/crm_wf_import.png)

对于导入活动， **CRM Connector活动配置步骤** :

1. 选择一个 **[!UICONTROL Import from the CRM]** 操作。
1. 转到下 **[!UICONTROL Remote object]** 拉列表，选择进程所关注的对象。 此对象与在连接器配置期间在Adobe Campaign中创建的一个表重合。
1. 转到部 **[!UICONTROL Remote fields]** 分并输入要导入的字段。

   要添加字段，请单击工 **[!UICONTROL Add]** 具栏中的按钮，然后单击图 **[!UICONTROL Edit expression]** 标。

   ![](assets/crm_task_import_add_field.png)

   如有必要，请通过列的下拉列表更改数据格 **[!UICONTROL Conversion]** 式。 可能的转换类型以数据格式 [详细介绍](#data-format)。

   >[!CAUTION]
   >
   >在CRM中和Adobe Campaign中链接对象时，CRM中记录的标识符是必填的。 在批准包装盒时，会自动添加该包装盒。
   >
   >对于增量数据导入，CRM端的上次修改日期也是必需的。

1. 您还可以根据需要筛选要导入的数据。 要执行此操作，请单击链 **[!UICONTROL Edit the filter...]** 接。

   在以下示例中，Adobe Campaign将仅导入自2012年11月1日起已为其记录某些活动的联系人。

   ![](assets/crm_task_import_filter.png)

   >[!CAUTION]
   >
   >过滤数据中详细介绍了与数据过滤模式关联 [的限制](#filtering-data)。

1. 通过 **[!UICONTROL Use automatic index...]** 此选项，您可以根据日期和上次修改日期自动管理CRM和Adobe Campaign之间的增量对象同步。

   For more on this, refer to [Variable management](#variable-management).

#### 变量管理 {#variable-management}

通过启用 **[!UICONTROL Automatic index]** 此选项，您只能收集自上次导入以来修改的对象。

![](assets/crm_task_import_option.png)

上次同步的日期默认存储在配置窗口中指定的选项中： **LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**。

>[!NOTE]
>
>此注释仅适用于通用活 **[!UICONTROL CRM Connector]** 动。 对于其他CRM活动，该过程是自动的。
>
>必须在 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** >下手动创建并填充此选项 **[!UICONTROL Options]**。 它必须是文本选项，并且其值需要与以下格式匹配：yyyy/ **MM/dd hh:mm:ss**。
> 
>您需要手动更新此选项才能进行进一步的导入。

您可以指定要考虑的远程CRM字段，以标识最近的更改。

默认情况下，将使用以下字段（按指定顺序）:

* 对于Microsoft Dynamics:已 **修改**,
* 对于Oracle On Demand: **LastUpdated**, **ModifiedDate**, **LastLoggedIn**,
* 对于Salesforce.com: **LastModifiedDate**, **SystemModstamp**。

激活选 **[!UICONTROL Automatic index]** 项会生成三个变量，这些变量可以通过类型活动在同步工作流中 **[!UICONTROL JavaScript code]** 使用。 这些活动包括：

* **vars.crmOptionName**:表示包含上次导入日期的选项的名称。
* **vars.crmStartImport**:表示上次数据恢复的开始日期（包括）。
* **vars.crmEndDate**:表示上次数据恢复的结束日期（不包括）。

   >[!NOTE]
   >
   >这些日期以下列格式显示：yyyy/ **MM/dd hh:mm:ss**。

#### 筛选数据 {#filtering-data}

为确保使用各种CRM进行高效操作，需要使用以下规则创建筛选器：

* 每个过滤级别只能使用一种类型的运算符。
* 不支持AND NOT运算符。
* 比较可能只涉及null值(&#39;is empty&#39;/&#39;is not empty&#39; type)或数字。 这意味着将评估值（右侧列），此评估的结果必须是数字。 因此不支持JOIN类型比较。
* 右侧列中包含的值将用JavaScript进行评估。
* 不支持JOIN比较。
* 左列中的表达式必须是字段。 它不能是多个表达式、数字等的组合。

例如，以下筛选条件对于CRM导入无效，因为OR运算符与AND运算符位于同一级别：

* OR运算符与AND运算符位于相同级别
* 对文本字符串进行比较。

![](assets/crm_import_wrong_filter.png)

#### 订购依据 {#order-by}

在Microsoft Dynamics和Salesforce.com中，可以按升序或降序对要导入的远程字段进行排序。

为此，请单击链 **[!UICONTROL Order by]** 接并将列添加到列表。

列表中各列的顺序是排序顺序：

![](assets/crm_import_order.png)

#### 记录标识 {#record-identification}

您可以使用在工作流中预先计算的人群，而不是导入CRM中包含的元素（并且可能已过滤）。

为此，请选择选 **[!UICONTROL Use the population calculated upstream]** 项并指定包含远程标识符的字段。

然后，选择要导入的入站人口字段，如下所示：

![](assets/crm_wf_import_calculated_population.png)

### 导出到CRM {#exporting-to-the-crm}

将Adobe Campaign数据导出到CRM中，可让您将整个内容复制到CRM数据库。

要将数据导出到CRM，您需要创建以下类型的工作流：

![](assets/crm_export_diagram.png)

对于导出，请将以下配置应用于 **CRM连接器活动** :

1. 选择一个 **[!UICONTROL Export to CRM]** 操作。
1. 转到下 **[!UICONTROL Remote object]** 拉列表，选择进程所关注的对象。 此对象与在连接器配置期间在Adobe Campaign中创建的一个表重合。

   >[!CAUTION]
   >
   >**CRM Connectors活动的导出功能** ，可在CRM端插入或更新字段。 要在CRM中启用字段更新，您需要指定远程表的主键。 如果缺少密钥，则将插入数据（而非更新）。

1. 在部 **[!UICONTROL Mapping]** 分中，指定要导出的字段及其在CRM中的映射。

   ![](assets/crm_export_config.png)

   要添加字段，请单击工 **[!UICONTROL Add]** 具栏中的按钮，然后单击图 **[!UICONTROL Edit expression]** 标。

   >[!NOTE]
   >
   >对于给定字段，如果CRM端没有定义匹配项，则无法更新这些值：它们会直接插入到CRM中。

   如有必要，请通过列的下拉列表更改数据格 **[!UICONTROL Conversion]** 式。 可能的转换类型以数据格式 [详细介绍](#data-format)。

   >[!NOTE]
   >
   >要导出的记录列表和导出结果将保存在临时文件中，该临时文件在工作流完成或重新启动之前一直可访问。 这样，您就可以在出错时重新开始该过程，而不会多次导出相同记录或丢失数据。

### 其他配置 {#additional-configurations}

#### 数据格式 {#data-format}

在将数据格式导入CRM或从CRM导入数据格式时，您可以立即转换它们。

为此，请选择要在匹配列中应用的转换。

![](assets/crm_task_import.png)

该模 **[!UICONTROL Default]** 式应用自动数据转换，在大多数情况下，这等于数据的复制／粘贴。 但是，时区管理会被应用。

其他可能的转化包括：

* **[!UICONTROL Date only]**:此模式将删除“日期+时间”类型字段。
* **[!UICONTROL Without time offset]**:此模式取消在默认模式中应用的时区管理。
* **[!UICONTROL Copy/Paste]**:此模式使用字符串等原始数据（无转换）。

#### 错误处理 {#error-processing}

在数据导入或导出的框架中，可以对错误和拒绝应用特定进程。 为此，请在选项卡 **[!UICONTROL Process rejects]** 中选 **[!UICONTROL Process errors]** 择和 **[!UICONTROL Behavior]** 选项。

![](assets/crm_export_options.png)

这些选项会放置匹配的输出过渡。

![](assets/crm_export_transitions.png)

然后，放置与要应用的流程相关的活动。

要处理实例的错误，可添加等待框并计划重试。

系统会收集包含其错误代码和相关消息的拒绝，这意味着您可以设置拒绝跟踪以优化同步过程。

>[!NOTE]
>
>即使未启 **[!UICONTROL Process rejects]** 用该选项，也会为每个被拒绝的列生成警告，并显示错误代码和消息。

通过 **[!UICONTROL Reject]** 输出过渡，您可以访问输出架构，该架构包含与错误消息和代码相关的特定列。 这些列包括：

* 对于Oracle On Demand: **errorLogFilename** （Oracle端的日志文件名）, **errorCode** （错误代码）, **errorSymbol** （错误符号，与错误代码不同）, **** errorMessageDescription（error context的说明）。
* 对于Salesforce.com: **errorSymbol** （错误符号，与错误代码不同）, **errorMessage** （错误上下文的描述）。

### 导入在CRM中删除的对象 {#importing-objects-deleted-in-the-crm}

要启用广泛的数据同步过程的设置，您可以将CRM中删除的对象导入Adobe Campaign。

为此，请应用以下步骤：

1. 选择一个 **[!UICONTROL Import objects deleted in the CRM]** 操作。
1. 转到下 **[!UICONTROL Remote object]** 拉列表，选择进程所关注的对象。 此对象与在连接器配置期间在Adobe Campaign中创建的一个表重合。
1. 在和字段中指定要考虑的删 **[!UICONTROL Start date]** 除期 **[!UICONTROL End date]** 限。 这些日期将包括在该期间内。

   ![](assets/crm_import_deleted_obj.png)

   >[!CAUTION]
   >
   >元素删除期必须与CRM的特定限制一致。 这意味着，例如，对于Salesforce.com,30天前删除的元素无法恢复。

### 在CRM中删除对象 {#deleting-objects-in-the-crm}

要删除CRM端的对象，您需要指定要删除的远程元素的主键。

![](assets/crm_delete_in_crm.png)

通过 **[!UICONTROL Behavior]** 该选项卡可以启用拒绝的处理。 此选项为活动生成第二个输出过 **[!UICONTROL CRM connector]** 渡。 For more on this, refer to [Error processing](#error-processing).

>[!NOTE]
>
>即使禁用 **[!UICONTROL Process rejects]** 了该选项，也会为每个被拒绝的列生成警告。

