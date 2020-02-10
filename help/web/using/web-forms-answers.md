---
title: Web表单答案
seo-title: Web表单答案
description: Web表单答案
seo-description: null
page-status-flag: never-activated
uuid: 374df070-8969-4bf6-bd24-0b827d38593f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: c89926b6-488e-4c72-8f67-b6af388bade3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Web表单答案{#web-forms-answers}

## 响应存储字段 {#response-storage-fields}

表单的答案可以保存在数据库的字段中，也可以临时保存在本地变量中。 在字段创建过程中将选择答案的存储模式。 可通过链接编辑该 **[!UICONTROL Edit storage...]** 内容。

对于表单中的每个输入字段，可以使用以下存储选项：

![](assets/s_ncs_admin_survey_select_storage.png)

* **[!UICONTROL Edit a recipient]**

   您可以选择数据库的字段：用户的答案将存储在此字段中。 对于每个用户，仅保存最后输入的值：它添加到其配置文件中：请参阅将 [数据存储在数据库中](#storing-data-in-the-database)。

* **[!UICONTROL Variable]**

   如果不想在数据库中存储信息，可以使用变量。 局部变量可声明为上游。 请参阅将 [数据存储在本地变量中](#storing-data-in-a-local-variable)。

### 将数据存储在数据库中 {#storing-data-in-the-database}

要将数据保存在数据库的现有字段中，请单击该图 **[!UICONTROL Edit expression]** 标，然后从可用字段列表中选择它。

![](assets/s_ncs_admin_survey_storage_type1.png)

>[!NOTE]
>
>默认的参考文档是 **nms:recipient** schema。 要查看表单或选择新表单，请从列表中选择表单，然后单击按 **[!UICONTROL Properties]** 钮。

### 将数据存储在本地变量中 {#storing-data-in-a-local-variable}

您可以使用局部变量，这样即使数据不存储在数据库中，也可以在页面或其他页面上重复使用数据，例如在显示字段时放置条件或个性化消息。

这意味着您可以使用未保存字段的值来授权在页面上显示一组选项。 在下面的页面中，车辆类型不存储在数据库中：

![](assets/s_ncs_admin_survey_no_storage_variable.png)

它存储在创建下拉框时必须选择的变量中，或者通过链接 **[!UICONTROL Edit storage...]** 选择。

![](assets/s_ncs_admin_survey_no_storage_variable2.png)

您可以显示现有变量并通过链接创建新 **[!UICONTROL Edit variables...]** 变量。 单击 **[!UICONTROL Add]** 按钮可创建新变量。

![](assets/s_ncs_admin_survey_add_a_variable.png)

创建页面的输入字段后，添加的变量将显示在本地变量列表中。

>[!NOTE]
>
>对于每个表单，您可以在上游创建变量。 为此，请选择表单并单击按 **[!UICONTROL Properties]** 钮。 该选 **[!UICONTROL Variables]** 项卡包含表单的本地变量。

**具有调节功能的本地存储的示例**

在上例中，仅当从下拉列表中选择了选项时，才显示包含有关私人车辆数据的容器，如可见性条件中所示： **[!UICONTROL Private]**

![](assets/s_ncs_admin_survey_add_a_condition.png)

如果用户选择私人车辆，Web表单将提供以下选项：

![](assets/s_ncs_admin_survey_no_storage_conda.png)

如果选择“专业”选项（如可见性条件所示），则将显示包含有关商用车辆的数据的容器：

![](assets/s_ncs_admin_survey_view_a_condition.png)

这意味着，如果用户选择商用车，则表单提供以下选项：

![](assets/s_ncs_admin_survey_no_storage_condb.png)

## 使用收集的信息 {#using-collected-information}

对于每个表单，提供的答案可在字段或标签中重新使用。 必须使用以下语法：

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
   >与其他字段不同， `<%=` 其字符将替换为转义字符，HTML内容将使用语法按原样保 `<%==` 存。

## 保存Web表单答案 {#saving-web-forms-answers}

要保存在表单页面中收集的信息，您需要在图中放置一个存储框。

![](assets/s_ncs_admin_survey_save_box.png)

使用此框有两种方法：

* 如果通过电子邮件中发送的链接访问Web表单，并且访问应用程序的用户已经在数据库中，则可以选中该选 **[!UICONTROL Update the preloaded record]** 项。 有关此问题的详细信息，请参 [阅通过电子邮件传送表单](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email)。

   在这种情况下，Adobe Campaign会使用用户配置文件的加密主密钥，Adobe Campaign会为每个配置文件分配一个唯一标识符。 您需要配置信息以通过预加载框预加载。 有关详细信息，请参 [阅预加载表单数据](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data)。

   >[!CAUTION]
   >
   >此选项将覆盖用户数据，如果有要在其中输入该数据的字段，则包括电子邮件地址。 它不能用于创建新配置文件，并且需要使用表单中的预加载框。

* 要丰富数据库中收件人的数据，请编辑存储框并选择对帐密钥。 对于内部使用（通常是内部网系统）或用于创建新配置文件（例如）的表单，您可以选择对帐字段。 该框提供Web应用程序各个页面中使用的数据库的所有字段：

   ![](assets/s_ncs_admin_survey_save_box_edit.png)

默认情况下，数据通过以下操作导入到数 **[!UICONTROL Update or insertion]** 据库：如果元素存在于数据库中，则会更新该元素（例如，选定的Newsletter或输入的电子邮件地址）。 如果信息不存在，则会添加该信息。

但是，您可以更改此行为。 为此，请选择元素的根，然后从下拉列表中选择要执行的操作：

![](assets/s_ncs_admin_survey_save_operation.png)

您可以选择要进行对帐的搜索文件夹和新配置文件的创建文件夹。 如果这些字段为空，则会在操作员的默认文件夹中搜索并创建配置文件。

>[!NOTE]
>
>可能的操作包括： **[!UICONTROL Simple reconciliation]**, **[!UICONTROL Update or insertion]**, **[!UICONTROL Insertion]**, **[!UICONTROL Update]**, **[!UICONTROL Deletion]**.\
>操作符的默认文件夹是操作员具有写入权限的第一个文件夹。\
>Refer to [this section](../../platform/using/access-management.md).

