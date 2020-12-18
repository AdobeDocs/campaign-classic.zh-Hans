---
solution: Campaign Classic
product: campaign
title: CRM Connector
description: 进一步了解CRM连接器并配置数据同步
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1520'
ht-degree: 0%

---


# CRM Connector{#crm-connector}

使用&#x200B;**CRM连接器**&#x200B;可以配置Adobe Campaign与CRM之间的数据同步。

有关Adobe Campaign中CRM连接器的详细信息，请参阅此[部分](../../platform/using/crm-connectors.md)。

这意味着您可以：

* 从CRM导入（请参阅[从CRM](#importing-from-the-crm)导入）,
* 导出到CRM（请参阅[导出到CRM](#exporting-to-the-crm)）,
* 导入CRM中删除的对象（请参阅[导入CRM](#importing-objects-deleted-in-the-crm)中删除的对象）,
* 删除CRM中的对象（请参阅[删除CRM](#deleting-objects-in-the-crm)中的对象）。

![](assets/crm_task_select_op.png)

选择与要配置同步的CRM匹配的外部帐户，然后选择要同步的对象（帐户、业务机会、联系人等）。

![](assets/crm_task_select_obj.png)

此活动的配置取决于要执行的过程。 下面详细介绍了各种配置。

## 从CRM {#importing-from-the-crm}导入

要在Adobe Campaign中通过CRM导入数据，您需要创建以下类型的工作流：

![](assets/crm_wf_import.png)

对于导入活动,**CRM连接器**&#x200B;活动配置步骤为：

1. 选择&#x200B;**[!UICONTROL Import from the CRM]**&#x200B;操作。
1. 转到&#x200B;**[!UICONTROL Remote object]**&#x200B;下拉列表并选择进程所关注的对象。 此对象与连接器配置期间在Adobe Campaign中创建的一个表重合。
1. 转到&#x200B;**[!UICONTROL Remote fields]**&#x200B;部分并输入要导入的字段。

   要添加字段，请单击工具栏中的&#x200B;**[!UICONTROL Add]**&#x200B;按钮，然后单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;图标。

   ![](assets/crm_task_import_add_field.png)

   如有必要，请通过&#x200B;**[!UICONTROL Conversion]**&#x200B;列的下拉列表更改数据格式。 此[页面](../../platform/using/crm-connectors.md#data-format)中详细介绍了可能的转换类型。

   >[!CAUTION]
   >
   >对于在CRM中和在Adobe Campaign中链接对象，CRM中记录的标识符是必需的。 活动获得批准后，系统会自动添加该组件。
   > 
   >对于增量数据导入，CRM端的上次修改日期也是必需的。

1. 您还可以根据需要过滤要导入的数据。 为此，请单击&#x200B;**[!UICONTROL Edit the filter...]**&#x200B;链接。

   在以下示例中，Adobe Campaign将仅导入自2012年7月31日以来已记录某些活动的联系人。

   ![](assets/crm_task_import_filter.png)

   [对数据进行筛选](#filter-on-data)部分详细介绍了与数据筛选模式链接的限制。

1. 使用&#x200B;**[!UICONTROL Use automatic index]**&#x200B;选项，您可以自动管理CRM和Adobe Campaign之间的增量对象同步，具体取决于日期及其上次修改时间。

   有关详细信息，请参阅[变量管理](#variable-management)。

## 变量管理{#variable-management}

启用&#x200B;**[!UICONTROL Automatic index]**&#x200B;选项可仅收集自上次导入以来修改的对象。

![](assets/crm_task_import_option.png)

上次同步的日期默认存储在配置窗口中指定的选项中：

```
LASTIMPORT_<%=instance.internalName%>_<%=activityName%>
```

您可以指定要考虑的远程CRM字段，以标识最新更改。

默认情况下，将使用以下字段（按指定顺序）:

* 对于Microsoft Dynamics:**已修改**,
* oracle点播：**LastUpdated**、**ModifiedDate**、**LastLoggedIn**、
* 对于Salesforce.com:**LastModifiedDate**、**SystemModstamp**。

激活&#x200B;**[!UICONTROL Automatic index]**&#x200B;选项会生成三个变量，这些变量可通过&#x200B;**[!UICONTROL JavaScript code]**&#x200B;类型活动在同步工作流中使用。 这些活动是：

* **varscrmOptionName**:表示包含上次导入日期的选项的名称。
* **vars.crmStartImport**:表示上次开始恢复的日期（包括）。
* **vars.crmEndDate**:表示上次数据恢复的结束日期（已排除）。

   这些日期以下列格式显示：**yyyy/MM/dd hh:mm:ss**。

## 对数据{#filter-on-data}进行过滤

要确保使用各种CRM进行高效操作，需要使用以下规则创建过滤器:

* 每个过滤级别只能使用一种类型的逻辑运算符。
* 不支持EXCEPT(AND NOT)运算符。
* 比较只能涉及null值(&#39;is empty&#39;/&#39;is not empty&#39; type)或数字。 这意味着一旦评估了&#x200B;**[!UICONTROL Value]**&#x200B;列（右侧列），此评估的结果必须是数字。
* **[!UICONTROL Value]**&#x200B;列中的数据用JavaScript进行评估。
* 不支持JOIN比较。
* 左栏中的表达式必须是字段。 它不能是多个表达式、数字等的组合。

例如，下面所示的过滤条件对CRM导入无效，因为：

* OR运算符与AND运算符位于同一级别。
* 对文本字符串进行比较。

![](assets/crm_import_wrong_filter.png)

## 排序依据{#order-by}

在Microsoft Dynamics和Salesforce.com中，可以按升序或降序对要导入的远程字段进行排序。

为此，请单击&#x200B;**[!UICONTROL Order by]**&#x200B;链接并将列添加到列表。

列表中的列顺序是排序顺序：

![](assets/crm_import_order.png)

## 记录标识{#record-identification}

您可以使用在工作流中预先计算的填充，而不是导入CRM中包含（可能已过滤）的元素。

为此，请选择&#x200B;**[!UICONTROL Use the population calculated upstream]**&#x200B;选项并指定包含远程标识符的字段。

然后选择要导入的入站人口的字段，如下所示：

![](assets/crm_wf_import_calculated_population.png)

## 导出到CRM {#exporting-to-the-crm}

将Adobe Campaign数据导出到CRM中，可将整个内容复制到CRM数据库。

要向CRM导出数据，您需要创建以下类型的工作流：

![](assets/crm_export_diagram.png)

对于导出，请将以下配置应用于&#x200B;**CRM连接器**&#x200B;活动:

1. 选择&#x200B;**[!UICONTROL Export to CRM]**&#x200B;操作。
1. 转到&#x200B;**[!UICONTROL Remote object]**&#x200B;下拉列表并选择进程所关注的对象。 此对象与连接器配置期间在Adobe Campaign中创建的一个表重合。

   >[!CAUTION]
   >
   >**CRM Connectors**&#x200B;活动的导出功能可在CRM端插入或更新字段。 要在CRM中启用字段更新，您需要指定远程表的主键。 如果缺少密钥，则将插入数据（而不是更新）。

1. 在&#x200B;**[!UICONTROL Mapping]**&#x200B;部分，指定要导出的字段及其在CRM中的映射。

   ![](assets/crm_export_config.png)

   要添加字段，请单击工具栏中的&#x200B;**[!UICONTROL Add]**&#x200B;按钮，然后单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;图标。

   对于给定字段，如果CRM端未定义匹配项，则无法更新这些值：它们直接插入到CRM中。

   如有必要，请通过&#x200B;**[!UICONTROL Conversion]**&#x200B;列的下拉列表更改数据格式。 此[部分](../../platform/using/crm-connectors.md#data-format)详细介绍了可能的转换类型。

   要导出的记录的列表和导出结果将保存在临时文件中，该临时文件在完成或重新启动工作流之前一直可供访问。 这使您能够在出错时再次开始该过程，而不会冒多次导出相同记录或丢失数据的风险。

## 数据格式和错误处理{#data-format-and-error-processing}

在将数据格式导入CRM或从CRM导入数据格式时，可以立即转换它们。

为此，请选择要在匹配列中应用的转换。

![](assets/crm_task_import.png)

**[!UICONTROL Default]**&#x200B;模式应用自动数据转换，在大多数情况下，这等于数据的复制／粘贴。 但是，时区管理被应用。

其他可能的转换包括：

* **[!UICONTROL Date only]**:此模式将删除“日期+时间”类型字段。
* **[!UICONTROL Without time offset]**:此模式取消在默认模式下应用的时区管理。
* **[!UICONTROL Copy/Paste]**:此模式使用字符串等原始数据（无转换）。

![](assets/crm_export_options.png)

在数据导入或导出框架中，可以对错误和拒绝应用特定流程。 为此，请在&#x200B;**[!UICONTROL Behavior]**&#x200B;选项卡中选择&#x200B;**[!UICONTROL Process rejects]**&#x200B;和&#x200B;**[!UICONTROL Process errors]**&#x200B;选项。

这些选项会放置匹配的出站过渡。

![](assets/crm_export_transitions.png)

然后，放置与要应用的流程相关的活动。

要处理实例的错误，您可以添加等待活动和计划工作流重试。

拒绝会收集到其错误代码和相关消息，这意味着您可以设置拒绝跟踪以优化同步过程。

即使&#x200B;**[!UICONTROL Process rejects]**&#x200B;选项未启用，也会为每个被拒绝列生成一个警告，并显示错误代码和消息。

**[!UICONTROL Reject]**&#x200B;出站过渡允许您访问包含与错误消息和代码相关的特定列的输出模式。 以下列为：

* oracle点播：**errorLogFilename**(Oracle侧日志文件的名称)、**errorCode**（错误代码）、**errorSymbol**（错误符号，不同于错误代码）、**errorMessage**（错误上下文的描述）。
* 对于Salesforce.com:**errorSymbol**（错误符号，不同于错误代码）,**errorMessage**（错误上下文的描述）。

## 正在导入CRM {#importing-objects-deleted-in-the-crm}中删除的对象

要启用广泛的数据同步过程的设置，您可以将CRM中删除的对象导入Adobe Campaign。

为此，请应用以下步骤：

1. 选择&#x200B;**[!UICONTROL Import objects deleted in the CRM]**&#x200B;操作。
1. 转到&#x200B;**[!UICONTROL Remote object]**&#x200B;下拉列表并选择进程所关注的对象。 此对象与连接器配置期间在Adobe Campaign中创建的一个表重合。
1. 在&#x200B;**[!UICONTROL Start date]**&#x200B;和&#x200B;**[!UICONTROL End date]**&#x200B;字段中指定要考虑的删除期。 这些日期将包括在该期间内。

   ![](assets/crm_import_deleted_obj.png)

   >[!CAUTION]
   >
   >元素删除期间必须与CRM特定的限制一致。 这意味着对于Salesforce.com，例如，30天前删除的元素无法恢复。

## 删除CRM {#deleting-objects-in-the-crm}中的对象

要删除CRM端的对象，您需要指定要删除的远程元素的主键。

![](assets/crm_delete_in_crm.png)

使用&#x200B;**[!UICONTROL Behavior]**&#x200B;选项卡可以启用拒绝的处理。 此选项为&#x200B;**[!UICONTROL CRM connector]**&#x200B;过渡生成第二个输出活动。 有关更多信息，请参阅此](../../platform/using/crm-connectors.md#error-processing)章节[。

即使禁用&#x200B;**[!UICONTROL Process rejects]**&#x200B;选项，也会为每个被拒绝的列生成警告。

## 如何配置联系人导入的示例{#example-of-how-to-configure-a-contact-import}

在以下示例中，活动配置为从Oracle点播CRM导入联系人。 在导入之前，将以某种方式选择CRM字段，使其与Adobe Campaign库中已存在的字段保持一致。

![](assets/crm_connectors_ood_6.png)

