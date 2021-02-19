---
solution: Campaign Classic
product: campaign
title: Web 窗体答案
description: Web 窗体答案
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 1%

---


# Web 窗体答案{#web-forms-answers}

## 响应存储字段{#response-storage-fields}

表单的答案可以保存在数据库的字段中或临时保存在本地变量中。 在创建字段时，将选择答案的存储模式。 可通过&#x200B;**[!UICONTROL Edit storage...]**&#x200B;链接编辑。

对于表单中的每个输入字段，提供以下存储选项：

![](assets/s_ncs_admin_survey_select_storage.png)

* **[!UICONTROL Edit a recipient]**

   您可以选择数据库的字段：用户答案将存储在此字段中。 对于每个用户，仅保存最后输入的值：在他们的用户档案中增加了：请参阅[在数据库中存储数据](#storing-data-in-the-database)。

* **[!UICONTROL Variable]**

   如果不想在数据库中存储信息，可以使用变量。 局部变量可声明为上游。 请参阅[将数据存储在本地变量](#storing-data-in-a-local-variable)中。

### 在数据库{#storing-data-in-the-database}中存储数据

要将数据保存在数据库的现有字段中，请单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;图标，然后从可用字段的列表中选择它。

![](assets/s_ncs_admin_survey_storage_type1.png)

>[!NOTE]
>
>默认引用文档为&#x200B;**nms:收件人**&#x200B;模式。 要视图表单或选择新表单，请从列表中选择表单，然后单击&#x200B;**[!UICONTROL Properties]**&#x200B;按钮。

### 将数据存储在本地变量{#storing-data-in-a-local-variable}中

您可以使用局部变量，这样即使数据未存储在数据库中，也可以在页面或其他页面上重复使用，例如在显示字段时放置条件或个性化消息。

这意味着您可以使用未保存字段的值授权在页面上显示一组选项。 在下面的页中，车辆类型未存储在数据库中：

![](assets/s_ncs_admin_survey_no_storage_variable.png)

它存储在创建下拉框时必须选择的变量中，或者通过&#x200B;**[!UICONTROL Edit storage...]**&#x200B;链接。

![](assets/s_ncs_admin_survey_no_storage_variable2.png)

您可以显示现有变量，并通过&#x200B;**[!UICONTROL Edit variables...]**&#x200B;链接创建新变量。 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以创建新变量。

![](assets/s_ncs_admin_survey_add_a_variable.png)

在创建页面的输入字段时，添加的变量将在局部变量的列表中可用。

>[!NOTE]
>
>对于每个表单，您可以在上游创建变量。 要执行此操作，请选择表单并单击&#x200B;**[!UICONTROL Properties]**&#x200B;按钮。 **[!UICONTROL Variables]**&#x200B;选项卡包含表单的本地变量。

**带条件的局部存储示例**

在上例中，仅当从下拉容器中选择&#x200B;**[!UICONTROL Private]**&#x200B;选项时，才显示包含有关私有车辆数据的列表，如可见性条件中所示：

![](assets/s_ncs_admin_survey_add_a_condition.png)

如果用户选择专用车辆，Web表单将优惠以下选项：

![](assets/s_ncs_admin_survey_no_storage_conda.png)

如果选择“专业”选项（如可见性条件所示），则将显示包含有关商用车数据的容器:

![](assets/s_ncs_admin_survey_view_a_condition.png)

这意味着，如果用户选择了商用车辆，表单将优惠以下选项：

![](assets/s_ncs_admin_survey_no_storage_condb.png)

## 使用收集的信息{#using-collected-information}

对于每个表单，提供的答案可在字段或标签中重复使用。 必须使用以下语法：

* 对于存储在数据库字段中的内容：

   ```
   <%=ctx.recipient.@field name%
   ```

* 对于存储在本地变量中的内容：

   ```
   <%= ctx.vars.variable name %
   ```

* 对于存储在HTML文本字段中的内容：

   ```
   <%== HTML field name %
   ```

   >[!NOTE]
   >
   >与将`<%=`字符替换为转义字符的其他字段不同，HTML内容会使用`<%==`语法按原样保存。

## 保存Web 窗体答案{#saving-web-forms-answers}

要保存在表单页面中收集的信息，您需要在图中放置一个存储框。

![](assets/s_ncs_admin_survey_save_box.png)

使用此框有两种方法：

* 如果通过电子邮件中发送的链接访问Web表单，并且访问应用程序的用户已在数据库中，则可以选中&#x200B;**[!UICONTROL Update the preloaded record]**&#x200B;选项。 有关详细信息，请参阅[通过电子邮件](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email)传送表单。

   在这种情况下，Adobe Campaign使用用户用户档案的加密主密钥，即按Adobe Campaign分配给每个用户档案的唯一标识符。 您需要通过预加载框配置要预加载的信息。 有关详细信息，请参阅[预加载表单数据](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)。

   >[!CAUTION]
   >
   >此选项将覆盖用户数据，包括要在其中输入该数据的字段时的电子邮件地址。 它不能用于创建新用户档案，并且需要在表单中使用预加载框。

* 要丰富收件人库中的存储数据，请编辑合并关键项框并选择数据。 对于内部使用（通常是内部网系统）或用于创建新用户档案（例如，）的表单，您可以选择对帐字段。 该框优惠Web 应用程序各页中使用的数据库的所有字段：

   ![](assets/s_ncs_admin_survey_save_box_edit.png)

默认情况下，数据通过&#x200B;**[!UICONTROL Update or insertion]**&#x200B;操作导入到数据库中：如果元素存在于数据库中，则会更新该元素（例如，已输入的选定新闻稿或电子邮件地址）。 如果信息不存在，则会添加该信息。

但是，您可以更改此行为。 要执行此操作，请选择元素的根，然后从下拉列表中选择要执行的操作：

![](assets/s_ncs_admin_survey_save_operation.png)

您可以选择要对帐的搜索文件夹和新用户档案的创建文件夹。 如果这些字段为空，则将搜索用户档案并在运算符的默认文件夹中创建。

>[!NOTE]
>
>可能的操作包括：**[!UICONTROL Simple reconciliation]**、**[!UICONTROL Update or insertion]**、**[!UICONTROL Insertion]**、**[!UICONTROL Update]**、**[!UICONTROL Deletion]**。\
>运算符的默认文件夹是运算符具有写权限的第一个文件夹。\
>请参阅[此章节](../../platform/using/access-management.md) 。

