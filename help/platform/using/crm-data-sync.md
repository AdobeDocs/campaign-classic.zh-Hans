---
product: campaign
title: CRM连接器数据同步
description: 管理Campaign和您的CRM之间的数据
feature: Microsoft CRM Integration, Salesforce Integration
exl-id: 7f9eda15-76e8-40a1-8302-004cea085778
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 1%

---

# 在Campaign和CRM之间同步数据 {#data-synchronization}



Adobe Campaign与CRM之间的数据同步是通过专用工作流活动执行的： [CRM连接器](../../workflow/using/crm-connector.md)。

例如，要将Microsoft Dynamics数据导入Adobe Campaign，请创建以下类型的工作流：

![](assets/crm_connectors_msdynamics_07.png)

此工作流通过Microsoft Dynamics导入联系人，将其与现有Adobe Campaign数据同步，删除重复联系人，并更新Adobe Campaign数据库。

需要配置&#x200B;**[!UICONTROL CRM Connector]**&#x200B;活动以同步数据。

![](assets/crm_connectors_msdynamics_08.png)

通过此活动，您可以：

* 从CRM导入 — [了解详情](#importing-from-the-crm)
* 导出到CRM - [了解详情](#exporting-to-the-crm)
* 导入CRM中删除的对象 — [了解更多](#importing-objects-deleted-in-the-crm)
* 删除CRM中的对象 — [了解更多](#deleting-objects-in-the-crm)

![](assets/crm_task_select_op.png)

选择与要配置同步的CRM匹配的外部帐户，然后选择要同步的对象：帐户、商机、潜在客户、联系人等。

![](assets/crm_task_select_obj.png)

此活动的配置取决于执行的流程。 各种配置详见下文。

## 从CRM导入 {#importing-from-the-crm}

要通过Adobe Campaign中的CRM导入数据，您需要创建以下类型的工作流：

![](assets/crm_wf_import.png)

对于导入活动，**[!UICONTROL CRM Connector]**&#x200B;活动配置步骤为：

1. 选择&#x200B;**[!UICONTROL Import from the CRM]**&#x200B;操作。
1. 转到&#x200B;**[!UICONTROL Remote object]**&#x200B;下拉列表并选择进程涉及的对象。 此对象与连接器配置期间在Adobe Campaign中创建的某个表一致。
1. 转到&#x200B;**[!UICONTROL Remote fields]**&#x200B;部分并输入要导入的字段。

   要添加字段，请单击工具栏中的&#x200B;**[!UICONTROL Add]**&#x200B;按钮，然后单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;图标。

   ![](assets/crm_task_import_add_field.png)

   如有必要，请通过&#x200B;**[!UICONTROL Conversion]**&#x200B;列的下拉列表更改数据格式。 以[数据格式](#data-format)详细列出了可能的转换类型。

   >[!IMPORTANT]
   >
   >CRM中记录的标识符对于链接CRM和Adobe Campaign中的对象是必需的。 该复选框在获得批准时自动添加。
   >
   >对于增量数据导入，CRM端的上次修改日期也是强制性的。

1. 您也可以根据需要筛选要导入的数据。 为此，请单击&#x200B;**[!UICONTROL Edit the filter...]**&#x200B;链接。

   在以下示例中，Adobe Campaign将仅导入自2012年11月1日以来记录了一些活动的联系人。

   ![](assets/crm_task_import_filter.png)

   >[!IMPORTANT]
   >
   >在[过滤数据](#filtering-data)中详细介绍了链接到数据过滤模式的限制。

1. 通过&#x200B;**[!UICONTROL Use automatic index...]**&#x200B;选项，您可以根据日期和上次修改时间，自动管理CRM和Adobe Campaign之间的增量对象同步。

   有关详细信息，请参阅[变量管理](#variable-management)。

### 管理变量 {#variable-management}

启用&#x200B;**[!UICONTROL Automatic index]**&#x200B;选项以仅收集自上次导入以来修改的对象。

![](assets/crm_task_import_option.png)

上次同步的日期存储在配置窗口中指定的选项中，默认情况下为： **LASTIMPORT_&lt;%=instance.internalName%>_&lt;%=activityName%>**。

>[!NOTE]
>
>此注释仅适用于通用&#x200B;**[!UICONTROL CRM Connector]**&#x200B;活动。 对于其他CRM活动，该流程是自动的。
>
>必须在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;下手动创建并填充此选项。 它必须是文本选项，其值需要匹配以下格式： **`yyyy/MM/dd hh:mm:ss`**。
> 
>您需要手动更新此选项以进行任何进一步的导入。

您可以指定要考虑的远程CRM字段以标识最新更改。

默认情况下，使用以下字段（按指定顺序）：

* 对于Microsoft Dynamics： **modifiedon**，
* 对于Salesforce.com： **LastModifiedDate**，**SystemModstamp**。

激活&#x200B;**[!UICONTROL Automatic index]**&#x200B;选项会生成三个变量，它们可以通过&#x200B;**[!UICONTROL JavaScript code]**&#x200B;类型活动在同步工作流中使用。 这些活动包括：

* **vars.crmOptionName**：表示包含上次导入日期的选项的名称。
* **vars.crmStartImport**：表示上次数据恢复的开始日期（包括）。
* **vars.crmEndDate**：表示上次数据恢复的结束日期（已排除）。

  >[!NOTE]
  >
  >这些日期以下列格式显示： **`yyyy/MM/dd hh:mm:ss`**。

### 筛选数据 {#filtering-data}

要确保各种CRM的高效运行，需要使用以下规则创建过滤器：

* 每个过滤级别只能使用一种类型的运算符。
* 不支持AND NOT运算符。
* 比较可能只涉及null值（“为空”/“不为空”类型）或数字。 这意味着将对值（右侧列）进行评估，且此评估的结果必须是数字。 因此，不支持JOIN类型比较。
* 右侧列中包含的值是在JavaScript中进行评估的。
* 不支持联接比较。
* 左侧列中的表达式必须为字段。 它不能是多个表达式、数字等的组合。

例如，以下筛选条件对于CRM导入将无效，因为OR运算符与AND运算符位于同一级别：

* OR运算符与AND运算符位于同一级别
* 对文本字符串进行比较

![](assets/crm_import_wrong_filter.png)

### 排序方式 {#order-by}

在Microsoft Dynamics和Salesforce.com中，您可以按升序或降序对要导入的远程字段进行排序。

为此，请单击&#x200B;**[!UICONTROL Order by]**&#x200B;链接并将列添加到列表中。

列表中的列顺序是排序顺序：

![](assets/crm_import_order.png)

### 记录标识 {#record-identification}

您可以使用工作流中预先计算的群体，而不是导入CRM中包含（并可能经过筛选）的元素。

为此，请选择&#x200B;**[!UICONTROL Use the population calculated upstream]**&#x200B;选项并指定包含远程标识符的字段。

然后，选择要导入的集客群体的字段，如下所示：

![](assets/crm_wf_import_calculated_population.png)

## 导出到CRM {#exporting-to-the-crm}

通过将Adobe Campaign数据导出到CRM，您可以将整个内容复制到CRM数据库。

要将数据导出到CRM，您需要创建以下类型的工作流：

![](assets/crm_export_diagram.png)

对于导出，请将以下配置应用于&#x200B;**[!UICONTROL CRM Connector]**&#x200B;活动：

1. 选择&#x200B;**[!UICONTROL Export to CRM]**&#x200B;操作。
1. 转到&#x200B;**[!UICONTROL Remote object]**&#x200B;下拉列表并选择进程涉及的对象。 此对象与连接器配置期间在Adobe Campaign中创建的某个表一致。

   >[!IMPORTANT]
   >
   >**[!UICONTROL CRM Connector]**&#x200B;活动的导出函数可以在CRM端插入或更新字段。 要在CRM中启用字段更新，您需要指定远程表的主键。 如果缺少键，将插入数据（而不是更新数据）。

1. 如果需要更快的导出，请勾选&#x200B;**[!UICONTROL Export in Batches]**。

   ![](assets/crm_export_config_2.png)

1. 在&#x200B;**[!UICONTROL Mapping]**&#x200B;部分中，单击&#x200B;**[!UICONTROL New]**&#x200B;以指定要导出的字段及其在CRM中的映射。

   ![](assets/crm_export_config.png)

   要添加字段，请单击工具栏中的&#x200B;**[!UICONTROL Add]**&#x200B;按钮，然后单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;图标。

   >[!NOTE]
   >
   >对于给定字段，如果在CRM端未定义匹配项，则无法更新值：这些值直接插入到CRM中。

   如有必要，请通过&#x200B;**[!UICONTROL Conversion]**&#x200B;列的下拉列表更改数据格式。 以[数据格式](#data-format)详细列出了可能的转换类型。

   >[!NOTE]
   >
   >要导出的记录列表和导出结果将保存在临时文件中，在工作流完成或重新启动之前，该文件将保持可访问状态。 这样，您就可以在出现错误时再次启动该过程，而不会出现多次导出同一记录或丢失数据的风险。

## 其他配置 {#additional-configurations}

### 数据格式 {#data-format}

将数据格式导入或从CRM导入时，您可以即时转换数据格式。

要实现此目的，请选择要应用于匹配列的转换。

![](assets/crm_task_import.png)

**[!UICONTROL Default]**&#x200B;模式应用自动数据转换，在大多数情况下相当于数据的复制/粘贴。 但是，会应用时区管理。

其他可能的转换包括：

* **[!UICONTROL Date only]**：此模式删除日期+时间类型字段。
* **[!UICONTROL Without time offset]**：此模式将取消在默认模式下应用的时区管理。
* **[!UICONTROL Copy/Paste]**：此模式使用原始数据，如字符串（无转换）。

### 错误处理 {#error-processing}

在数据导入或导出的框架中，您可以将特定进程应用于错误和拒绝。 为此，请在&#x200B;**[!UICONTROL Behavior]**&#x200B;选项卡中选择&#x200B;**[!UICONTROL Process rejects]**&#x200B;和&#x200B;**[!UICONTROL Process errors]**&#x200B;选项。

![](assets/crm_export_options.png)

这些选项可放置匹配的输出过渡。

![](assets/crm_export_transitions.png)

然后放置与要应用的进程相关的活动。

要处理实例错误，可以添加等待框并安排重试。

系统会收集拒绝及其错误代码和相关消息，这意味着您可以设置拒绝跟踪以优化同步过程。

>[!NOTE]
>
>即使未启用&#x200B;**[!UICONTROL Process rejects]**&#x200B;选项，也会为每个被拒绝的列生成带有错误代码和消息的警告。

通过&#x200B;**[!UICONTROL Reject]**&#x200B;输出转换，可访问包含与错误消息和代码相关的特定列的输出架构。 对于Salesforce.com，此列为&#x200B;**errorSymbol** （错误符号，不同于错误代码）、**errorMessage** （错误上下文的说明）。

## 导入CRM中删除的对象 {#importing-objects-deleted-in-the-crm}

要启用广泛的数据同步过程的设置，您可以将CRM中删除的对象导入Adobe Campaign。

要执行此操作，请应用以下步骤：

1. 选择&#x200B;**[!UICONTROL Import objects deleted in the CRM]**&#x200B;操作。
1. 转到&#x200B;**[!UICONTROL Remote object]**&#x200B;下拉列表并选择进程涉及的对象。 此对象与连接器配置期间在Adobe Campaign中创建的某个表一致。
1. 指定要在&#x200B;**[!UICONTROL Start date]**&#x200B;和&#x200B;**[!UICONTROL End date]**&#x200B;字段中考虑的删除时段。 这些日期将包含在此期间中。

   ![](assets/crm_import_deleted_obj.png)

   >[!IMPORTANT]
   >
   >元素删除期必须符合CRM的特定限制。 这意味着对于Salesforce.com ，例如，30天前删除的元素将无法恢复。

## 删除 CRM 中的对象 {#deleting-objects-in-the-crm}

要删除CRM端的对象，您需要指定要删除的远程元素的主键。

![](assets/crm_delete_in_crm.png)

**[!UICONTROL Behavior]**&#x200B;选项卡允许您启用拒绝处理。 此选项为&#x200B;**[!UICONTROL CRM connector]**&#x200B;活动生成第二个输出转换。 有关详情，请参阅[处理](#error-processing)时出错。

>[!NOTE]
>
>即使&#x200B;**[!UICONTROL Process rejects]**&#x200B;选项被禁用，也会为每个被拒绝的列生成警告。
>
