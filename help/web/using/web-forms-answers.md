---
product: campaign
title: Web窗体答案
description: Web窗体答案
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Web Forms
exl-id: 5d48bb27-1884-47f1-acb7-dff5113565bc
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 0%

---

# Web窗体答案{#web-forms-answers}


## 响应存储字段 {#response-storage-fields}

表单的答案可以保存在数据库的字段中，也可以暂时保存在本地变量中。 答案的存储模式是在字段创建期间选择的。 可以通过&#x200B;**[!UICONTROL Edit storage...]**&#x200B;链接进行编辑。

对于表单中的每个输入字段，可以使用以下存储选项：

![](assets/s_ncs_admin_survey_select_storage.png)

* **[!UICONTROL Edit a recipient]**

  您可以选择数据库的字段：用户的回答将存储在此字段中。 对于每个用户，仅保存最后输入的值：已添加到其配置文件中：请参阅[将数据存储在数据库中](#storing-data-in-the-database)。

* **[!UICONTROL Variable]**

  如果不想在数据库中存储信息，则可以使用变量。 可以上游声明局部变量。 请参阅[将数据存储在局部变量中](#storing-data-in-a-local-variable)。

### 将数据存储在数据库中 {#storing-data-in-the-database}

要将数据保存在数据库的现有字段中，请单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;图标，然后从可用字段列表中选择该数据。

![](assets/s_ncs_admin_survey_storage_type1.png)

>[!NOTE]
>
>默认参考文档是&#x200B;**nms：recipient**&#x200B;架构。 要查看它或选择新表单，请从列表中选择该表单，然后单击&#x200B;**[!UICONTROL Properties]**&#x200B;按钮。

### 将数据存储在局部变量中 {#storing-data-in-a-local-variable}

您可以使用本地变量，以便即使数据未存储在数据库中，也可以在页面或其他页面上重复使用，例如，在字段显示上放置条件或个性化消息。

这意味着您可以使用未保存字段的值来授权在页面上显示一组选项。 在下面的页面中，车辆类型未存储在数据库中：

![](assets/s_ncs_admin_survey_no_storage_variable.png)

它存储在变量中，创建下拉框或通过&#x200B;**[!UICONTROL Edit storage...]**&#x200B;链接时必须选择该变量。

![](assets/s_ncs_admin_survey_no_storage_variable2.png)

您可以通过&#x200B;**[!UICONTROL Edit variables...]**&#x200B;链接显示现有变量和创建新变量。 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以创建新变量。

![](assets/s_ncs_admin_survey_add_a_variable.png)

创建页面的输入字段后，添加的变量将显示在局部变量列表中。

>[!NOTE]
>
>对于每个表单，均可在上游创建变量。 为此，请选择该表单并单击&#x200B;**[!UICONTROL Properties]**&#x200B;按钮。 **[!UICONTROL Variables]**&#x200B;选项卡包含表单的局部变量。

**具有条件约束的本地存储示例**

在上述示例中，仅当从下拉列表中选择&#x200B;**[!UICONTROL Private]**&#x200B;选项时，才会显示包含有关私家车数据的容器，如可见性条件中所示：

![](assets/s_ncs_admin_survey_add_a_condition.png)

如果用户选择私家车，则Web窗体会提供以下选项：

![](assets/s_ncs_admin_survey_no_storage_conda.png)

如果选择“专业”选项，则会显示包含有关商用车辆数据的容器，如可见性条件所示：

![](assets/s_ncs_admin_survey_view_a_condition.png)

这意味着，如果用户选择商业车辆，则表单会提供以下选项：

![](assets/s_ncs_admin_survey_no_storage_condb.png)

## 使用收集的信息 {#using-collected-information}

对于每个表单，提供的答案可以在字段或标签中重复使用。 必须使用以下语法：

* 对于存储在数据库字段中的内容：

  ```
  <%=ctx.recipient.@field name%
  ```

* 对于存储在局部变量中的内容：

  ```
  <%= ctx.vars.variable name %
  ```

* 对于存储在HTML文本字段中的内容：

  ```
  <%== HTML field name %
  ```

  >[!NOTE]
  >
  >与其`<%=`字符被转义字符替换的其他字段不同，HTML内容使用`<%==`语法按原样保存。

## 保存Web窗体答案 {#saving-web-forms-answers}

要保存表单页面中收集的信息，需要在图中放置一个存储框。

![](assets/s_ncs_admin_survey_save_box.png)

可通过两种方式使用此框：

* 如果通过电子邮件中发送的链接访问Web窗体，并且访问应用程序的用户已在数据库中，则可以选中&#x200B;**[!UICONTROL Update the preloaded record]**&#x200B;选项。 有关详情，请参阅[通过电子邮件传递表单](publishing-a-web-form.md#delivering-a-form-via-email)。

  在这种情况下，Adobe Campaign使用用户配置文件的加密主密钥，即Adobe Campaign分配给每个配置文件的唯一标识符。 您需要通过预加载框将信息配置为预加载。 有关详细信息，请参阅[预加载表单数据](publishing-a-web-form.md#pre-loading-the-form-data)。

  >[!CAUTION]
  >
  >如果存在要输入用户数据的字段，则此选项会覆盖该数据，包括电子邮件地址。 不能使用它来创建新配置文件，并需要在表单中使用预加载框。

* 要扩充数据库中的收件人数据，请编辑存储框并选择协调密钥。 对于内部使用（通常是Intranet系统）或用于创建新用户档案的表单，您可以选择协调字段。 该框提供在Web应用程序的各个页面中使用的数据库的所有字段：

  ![](assets/s_ncs_admin_survey_save_box_edit.png)

默认情况下，数据通过&#x200B;**[!UICONTROL Update or insertion]**&#x200B;操作导入数据库：如果数据库中存在该数据，则会更新元素（例如，所选新闻稿或输入的电子邮件地址）。 如果该文件不存在，则会添加该信息。

但是，您可以更改此行为。 为此，请选择元素的根并从下拉列表中选择要执行的操作：

![](assets/s_ncs_admin_survey_save_operation.png)

您可以选择协调的搜索文件夹，也可以选择新配置文件的创建文件夹。 如果这些字段为空，则会在运算符的默认文件夹中搜索并创建用户档案。

>[!NOTE]
>
>可能的操作包括： **[!UICONTROL Simple reconciliation]**、**[!UICONTROL Update or insertion]**、**[!UICONTROL Insertion]**、**[!UICONTROL Update]**、**[!UICONTROL Deletion]**。\
>运算符的默认文件夹是运算符具有写入权限的第一个文件夹。\
>请参阅[此小节](../../platform/using/access-management.md)。
