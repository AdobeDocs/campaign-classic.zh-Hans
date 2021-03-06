---
product: campaign
title: 向 Web 窗体添加字段
description: 向 Web 窗体添加字段
feature: Web Forms, Landing Pages
exl-id: 827b6575-7206-4dfc-b2c6-b95a6d5730b1
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '2368'
ht-degree: 1%

---

# 向 Web 窗体添加字段{#adding-fields-to-a-web-form}

![](../../assets/common.svg)

在Web窗体中，字段允许用户输入信息并选择选项。 Web窗体可以提供输入字段、选择字段、静态和高级内容（捕获、订阅等）。

使用向导添加字段时，会根据所选字段或存储变量自动检测字段类型。 您可以使用 **[!UICONTROL Type]** 下拉框 **[!UICONTROL General]** 选项卡。

![](assets/s_ncs_admin_webform_change_type.png)

使用工具栏中的按钮时，选择要添加的字段类型。

提供以下类型的字段：

* 文本/数字输入。 请参阅 [添加输入字段](#adding-input-fields).
* 下拉列表选择。 请参阅 [添加下拉列表](#adding-drop-down-lists).
* 通过复选框进行多个选择。 请参阅 [添加复选框](#adding-checkboxes).
* 通过单选按钮进行排他性选择。 请参阅 [添加单选按钮](#adding-radio-buttons).
* 在选项网格中投票。 请参阅 [添加网格](#adding-grids).
* 数字和日期。 请参阅 [添加日期和数字](#adding-dates-and-numbers).
* 订阅/退订信息服务。 请参阅 [订阅复选框](#subscription-checkboxes).
* 验证码。 请参阅 [插入验证码](#inserting-a-captcha).
* “下载”按钮。 [上传文件](#uploading-a-file).
* 隐藏常量。 请参阅 [插入隐藏常量](#inserting-a-hidden-constant).

请指定响应存储模式：更新数据库中的字段（仅存储最后保存的值）或存储在变量中（不存储答案）。 有关更多信息，请参阅 [响应存储字段](web-forms-answers.md#response-storage-fields).

>[!NOTE]
>
>默认情况下，该字段会插入到当前树的底部。 使用工具栏中的箭头将其上移或下移。

## 字段创建向导 {#field-creation-wizard}

对于表单的每个页面，您可以通过工具栏中的第一个按钮添加字段。 要执行此操作，请转到 **[!UICONTROL Add using the wizard]** 菜单。

![](assets/s_ncs_admin_survey_add_field_menu.png)

选择要创建的字段类型：您可以选择在数据库中添加字段、变量，或导入在其他表单中创建并在容器中收集的一组字段。

单击 **[!UICONTROL Next]** ，然后选择存储字段或变量，或要导入的容器。

![](assets/s_ncs_admin_webform_wz_confirm_db.png)

单击 **[!UICONTROL Finish]** 将所选字段插入页面。

![](assets/s_ncs_admin_webform_wz_insert_field.png)

## 添加输入字段 {#adding-input-fields}

要添加输入字段，请单击 **[!UICONTROL Input control]** 按钮，然后选择要添加的字段类型。

![](assets/s_ncs_admin_webform_select_field.png)

### 输入字段的类型 {#types-of-input-fields}

可在表单页面中插入五种不同类型的文本字段：

* **文本**:允许用户在一行上输入文本。

   ![](assets/s_ncs_admin_survey_txt_ex.png)

* **数值**:允许用户在一行中输入数字。 有关更多信息，请参阅 [添加数字](#adding-numbers).

   页面获得批准后，将检查字段内容以确保输入的值与字段兼容。 有关更多信息，请参阅 [定义控制设置](form-rendering.md#defining-control-settings).

* **密码**:允许用户在一行上输入文本。 在文本输入期间，字符会被替换为句点：

   ![](assets/s_ncs_admin_survey_passwd_ex.png)

   >[!CAUTION]
   >
   >密码在数据库中存储时未加密。

* **多行文本**:允许用户在几行上输入文本。

   ![](assets/s_ncs_admin_survey_txtmulti_ex.png)

   >[!CAUTION]
   >
   >多行文本字段是可包含回车符的特定字段。 其存储空间必须与映射到XML元素的字段关联，而不是与XML属性关联。

* **扩充了多行文本**:允许用户输入将以HTML格式存储的布局的文本。

   ![](assets/s_ncs_admin_survey_txthtmli_ex.png)

   您可以选择提供给用户的编辑器类型。 为此，请使用 **[!UICONTROL HTML editor]** 字段 **[!UICONTROL Advanced]** 选项卡。

   ![](assets/webapp_enrich_text_type.png)

   显示的图标数量因编辑器类型而异。 对于 **[!UICONTROL Advanced]** 编辑器时，渲染将如下所示：

   ![](assets/webapp_enrich_text_max.png)

### 配置输入字段 {#configure-input-fields}

所有输入字段都基于同一模式使用以下选项进行配置：

![](assets/s_ncs_admin_survey_txt_param.png)

的 **[!UICONTROL General]** 选项卡，您可以输入字段的名称，并根据需要为其添加默认值。

答案存储模式可以通过 **[!UICONTROL Edit storage...]** 链接。 值可以存储在数据库的现有字段中；或者，您可以选择不在数据库中保存信息（使用本地变量）。

>[!NOTE]
>
>存储模式详见 [响应存储字段](web-forms-answers.md#response-storage-fields)

的 **[!UICONTROL Advanced]** 选项卡，用于为字段定义显示参数（标签位置、对齐方式等）。 请参阅 [定义Web窗体布局](defining-web-forms-layout.md).

## 添加下拉列表 {#adding-drop-down-lists}

您可以在调查页面中插入下拉列表。 这允许用户从下拉菜单中的选件值中选择一个值。

![](assets/s_ncs_admin_survey_dropdown_sample.png)

要向表单页面添加下拉框，请单击 **[!UICONTROL Selection controls > Drop-down list]** 按钮。

![](assets/s_ncs_admin_survey_create_dropdown.png)

选择答案存储模式并确认您的选择。

在 **[!UICONTROL General]** 选项卡。 如果信息存储在数据库的现有字段中，并且是枚举字段，则可以通过单击 **[!UICONTROL Initialize the list of values from the database]** ，如下所示：

![](assets/s_ncs_admin_survey_database_values.png)

>[!NOTE]
>
>使用值列表右侧的箭头可更改其顺序。

如果数据存储在链接的表中，则可以选择保存列表中建议值的字段。 例如，如果选择国家/地区表，请单击 **[!UICONTROL Initialize the list of values from the database...]** ，然后选择所需的字段。

![](assets/s_ncs_admin_survey_preload_values.png)

接下来，单击 **[!UICONTROL Load]** 链接以检索值：

![](assets/s_ncs_admin_survey_load_button.png)

>[!CAUTION]
>
>每当更新列表以刷新选件的值时，请重复此操作。

## 添加复选框 {#adding-checkboxes}

要使用户选择选项，您需要使用复选框。

![](assets/s_ncs_admin_survey_check_box.png)

要向表单添加复选框，请单击 **[!UICONTROL Selection controls > Checkbox...]** 图标。

选择答案存储模式并确认您的选择。

在 **[!UICONTROL Label]** 字段 **[!UICONTROL General]** 选项卡。

![](assets/s_ncs_admin_survey_check_box_edit.png)

通过复选框，您可以根据是否选中了该框，为存储字段（或值）分配值。 的 **[!UICONTROL Values]** 部分中，您可以输入在选中该框时要分配的值(在 **[!UICONTROL Value]** 字段)，以及在未选中时要分配的值(在 **[!UICONTROL Empty value]** 字段。 这些值取决于数据存储格式。

如果存储字段（或变量）是布尔值，则将自动推断未选中该框时要分配的值。 在这种情况下，仅 **[!UICONTROL Value if checked]** 字段，如下所示：

![](assets/s_ncs_admin_survey_check_box_enum.png)

## 示例：如果选中框，则为字段分配值 {#example--assign-a-value-to-a-field-if-a-box-is-checked}

我们希望在表单中插入一个复选框以发送维护请求，如下所示：

![](assets/s_ncs_admin_survey_check_box_ex.png)

该信息将上传到数据库和现有字段(在本例中， **[!UICONTROL Comment]** 字段):

![](assets/s_ncs_admin_survey_check_box_ex_list.png)

如果选中“Maintenance required”（需要维护）框，则 **[!UICONTROL Comment]** 列将包含“需要维护”。 如果未勾选该框，则列将显示“不需要维护”。 要获取此结果，请将以下配置应用到表单页面上的复选框：

![](assets/s_ncs_admin_survey_check_box_ex_edit.png)

## 添加单选按钮 {#adding-radio-buttons}

利用单选按钮，可为用户提供一系列可供选择的专用选项。 同一字段的值不同。

![](assets/s_ncs_admin_survey_radio_button.png)

您可以单独创建单选按钮（单一按钮）或通过多选项列表创建单选按钮，但由于单选按钮的要点是选择一个或另一个选项，因此我们将始终创建至少一对单选按钮，而不仅仅是单个按钮。

>[!CAUTION]
>
>要强制选择，您需要创建一个多选项列表。

### 添加单个按钮 {#add-single-buttons}

要向表单页面添加单选按钮，请转到 **[!UICONTROL Selection controls > Radio button]** 菜单，然后选择存储模式。

![](assets/s_ncs_admin_survey_radio_button_sample.png)

单选按钮的配置方式与复选框类似(请参阅 [添加复选框](#adding-checkboxes))。 但是，如果未选择选项，则不会分配任何值。 为了使多个按钮相互依赖，即选择一个按钮会自动取消选择其他按钮，这些按钮必须存储在同一字段中。 如果它们未存储在数据库中，则临时存储必须使用相同的本地变量。 请参阅 [响应存储字段](web-forms-answers.md#response-storage-fields).

### 添加按钮列表 {#add-a-list-of-buttons}

要通过列表添加单选按钮，请转到 **[!UICONTROL Selection controls>Multiple choice]** 菜单。

![](assets/s_ncs_admin_survey_radio_button_sample2.png)

添加任意数量的单选按钮以添加标签。 此功能的优势在于，您可以从现有字段（对于分项字段）中导入值，并使其允许用户选择一个选项。 但是，按钮的布局不那么灵活。

>[!NOTE]
>
>无法在Web应用程序中启用多选。
>但是，可以插入 **[!UICONTROL Multiple choice]** 在Web应用程序中键入字段，但这将不允许用户选择多个值。

## 添加网格 {#adding-grids}

网格用于在Web应用程序中设计投票页面。 这样，您就可以为回答调查或评估类型Web表单提供单选按钮列表，如下所示：

![](assets/s_ncs_admin_survey_vote_param.png)

要在表单中使用此类型的元素，请创建一个简单的网格，并为要评估的每个元素添加一行。

![](assets/s_ncs_admin_survey_vote_sample.png)

网格每行中的单选按钮数与简单网格中定义的值数匹配。

![](assets/s_ncs_admin_survey_vote_ex.png)

每个网格行只能选择一个选项。

>[!NOTE]
>
>在本例中，网格的标签处于隐藏状态。 要执行此操作，请转到 **[!UICONTROL Advanced]** 选项卡 **[!UICONTROL Label position]** 显示定义为 **[!UICONTROL Hidden]** . 请参阅 [定义标签的位置](defining-web-forms-layout.md#defining-the-position-of-labels).

## 添加日期和数字 {#adding-dates-and-numbers}

表单字段的内容可以格式化以匹配存储在数据库中的数据或满足特定要求。 您可以创建用于输入数字和日期的合适字段。

### 添加日期 {#adding-dates}

![](assets/s_ncs_admin_survey_date_calendar.png)

要允许用户在表单页面中输入日期，请添加输入字段并选择类型 **[!UICONTROL Date...]**.

输入字段的标签并配置数据存储模式。

![](assets/s_ncs_admin_survey_date_edit.png)

利用窗口的下部分，可为存储在此字段中的值选择日期和时间格式。

![](assets/s_ncs_admin_survey_date_edit_values.png)

您还可以选择不显示日期（或时间）。

日期可通过日历或下拉框选择。 您也可以直接在字段中输入这些参数，但需要匹配上面屏幕中指定的格式。

>[!NOTE]
>
>默认情况下，表单中使用的日期通过日历输入。 对于多语言表单，请检查日历是否在使用的所有语言版本。 请参阅 [翻译Web窗体](translating-a-web-form.md).

但是，在某些情况下（例如，输入出生日期），使用下拉列表可能会比较容易。

![](assets/s_ncs_admin_survey_date_list_select.png)

为此，请单击 **[!UICONTROL Advanced]** ，然后使用 **[!UICONTROL Drop-down lists]**.

![](assets/s_ncs_admin_survey_date_selection.png)

然后，您可以设置对列表中提供的值的限制。

![](assets/s_ncs_admin_survey_date_first_last_y.png)

### 添加数字 {#adding-numbers}

您可以为数字的输入创建适当的字段。

![](assets/s_ncs_admin_survey_number.png)

在数字字段中，用户只能输入数字。 页面获得批准后，将自动应用登入控件。

根据数据库中存储数据的字段，可能会应用特殊格式或某些限制。 您还可以指定最大值和最小值。 此类型的字段配置如下：

![](assets/s_ncs_admin_survey_number_edit.png)

默认值是发布表单时在字段中显示的值。 用户可以更正此问题。

您可以通过 **[!UICONTROL Advanced]** 选项卡，如下所示：

![](assets/s_ncs_admin_survey_number_ex_conf.png)

在形式中，渲染将如下所示：

![](assets/s_ncs_admin_survey_number_ex.png)

## 订阅复选框 {#subscription-checkboxes}

您可以添加控件，以允许用户订阅或退订一个或多个信息服务（新闻稿、警告、实时通知等）。 要订阅，用户将检查相应的服务。

要创建订阅复选框，请单击 **[!UICONTROL Advanced controls>Subscription]**.

![](assets/s_ncs_admin_survey_subscription_edit.png)

指示复选框的标签，并使用 **[!UICONTROL Service]** 下拉框。

>[!NOTE]
>
>信息服务详见 [本页](../../delivery/using/managing-subscriptions.md).

用户通过勾选相关选项订阅了服务。

![](assets/s_ncs_admin_survey_subscribe.png)

>[!CAUTION]
>
>如果用户已订阅了信息服务，并且在批准表单时未勾选链接到此服务的框，则他们将被取消订阅。

## 插入验证码 {#inserting-a-captcha}

的目的 **验证码** 测试旨在防止您的Web表单被欺骗性使用。

>[!CAUTION]
>
>如果您的表单包含多个页面，则必须始终将验证码放在最后一页（即存储盒之前），以防安全措施受到任何规避。

要将验证码插入表单，请单击工具栏上的第一个按钮，然后选择 **[!UICONTROL Advanced controls>Captcha]**.

![](assets/s_ncs_admin_survey_add_captcha.png)

输入字段的标签。 此标签将显示在Captcha显示区域的前面。 您可以在 **[!UICONTROL Advanced]** 选项卡。

![](assets/s_ncs_admin_survey_captcha_adv.png)

>[!NOTE]
>
>对于 **[!UICONTROL captcha]** 类型控件，则无需指示存储字段或变量。

验证码会插入到页面中，并在可视化下方放置一个输入字段。 这两个元素是密不可分的，在页面布局中，它们被视为单个项目（占用一个单元格）。

![](assets/s_ncs_admin_survey_captcha_sample.png)

确认页面后，如果验证码内容未正确输入，则输入字段将以红色显示。

![](assets/s_ncs_admin_survey_captcha_error.png)

您可以创建要显示的错误消息。 要实现此目的，请使用 **[!UICONTROL Personalize the message]** 链接 **[!UICONTROL General]** 选项卡。

![](assets/s_ncs_admin_survey_captcha_error_msg.png)

>[!NOTE]
>
>捕获码始终为8个字符长。 您无法修改此值。

## 上传文件 {#uploading-a-file}

您可以向页面添加上传字段。 例如，此功能对于Intranet文件共享非常有用。

![](assets/s_ncs_admin_survey_download_file.png)

要向表单页面插入上传字段，请选择 **[!UICONTROL Advanced controls > File...]** 菜单。

默认情况下，上传的文件会存储在可通过 **[!UICONTROL Resources > Online > Public resources]** 菜单。 您可以使用脚本更改此行为。 此脚本可以使用 [Campaign JSAPI文档](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hans)，包括涉及文件操作的用户。

您可以将指向这些文件的链接存储在本地变量或数据库字段中。 例如，您可以扩展收件人模式，以添加指向基于文件的资源的链接。

>[!CAUTION]
>
>* 此类文件必须为具有安全访问（使用凭据）的表单保留。
>* Adobe Campaign不会控制上传的资源的大小或类型：因此，我们强烈建议仅将上载字段用于安全类型的内联网站点。
>* 如果多个服务器已链接到实例（负载平衡架构），则需要确保对Web表单的调用到达同一服务器。
>* 这些实施需要Adobe Campaign咨询团队的帮助。
>


## 插入隐藏常量 {#inserting-a-hidden-constant}

当用户验证表单的其中一个页面时，您可以将特定值设置为其用户档案的字段或变量。

此字段对用户不可见，但可用于扩充用户配置文件中的数据。

为此，请在 **常量** ，并指定值和存储位置。

在以下示例中， **来源** 每当用户批准此页面时，都会自动填写收件人用户档案的字段。 该常量不显示在页面上。

![](assets/s_ncs_admin_survey_constante.png)
