---
title: 导出数据
seo-title: 导出数据
description: 导出数据
seo-description: null
page-status-flag: never-activated
uuid: 818de79a-587f-4735-b333-4bc702c3b450
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: fecadb66-b81d-4fb6-9971-7bfd024d70b7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b690e6c7141ba88c8ce72f631ec24fc068ade8f5
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 59%

---


# 导出数据{#exporting-data}

## 导出向导 {#export-wizard}

导出参数通过向导记录。通用导出模块作为标准提供，允许您从数据库存取和提取数据：联系人、客户、清单、细分等。例如，在电子表格中使用广告系列追踪数据（追踪历史记录等）非常有用。输出数据可以是 txt、CSV、TAB 或 XML 格式。

### 第 1 步 - 选择导出模板 {#step-1---choosing-the-export-template}

启动导出向导时，首先必须选择模板。例如，要配置最近注册的收件人的导出，请按照以下步骤操作：

1. 选择文 **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** 件夹。
1. 点击 **New**，然后点击 **Export** 以创建导出模板。

   ![](assets/s_ncs_user_export_wizard01.png)

1. Click the arrow to the right of the **[!UICONTROL Export template]** field to select your template, or click **[!UICONTROL Select link]** to browse the tree.

   本机模板为 **[!UICONTROL New text export]**。 不得修改此模板，但您可以复制它以配置新模板。By default, export templates are saved in the **[!UICONTROL Resources > Templates > Job templates]** node.

1. Enter a name for export in the **[!UICONTROL Label]** field. 您可以添加描述。
1. 选择导出类型。有两种可能的导出类型： **[!UICONTROL Simple export]** 只导出一个文件，并 **[!UICONTROL Multiple export]** 在一次执行中从一种或多种类型的源文档导出多个文件。

### 第 2 步 - 要导出的文件类型 {#step-2---type-of-file-to-export}

选择要导出的文档类型，即要导出的数据模式。

By default, when the export is launched from the **[!UICONTROL Jobs]** node the data comes from the recipient table. When the export is launched from a list of data (from the **[!UICONTROL right click > Export]** menu), the table to which the data belongs is automatically filled in in the **[!UICONTROL Document type]** field.

![](assets/s_ncs_user_export_wizard02.png)

* By default, the **[!UICONTROL Download the file generated on the server after the export]** option is selected. In the **[!UICONTROL Local file]** field, fill in the name and path of the file to be created, or browse your local disk by clicking the folder to the right of the field. 您可以取消选择此选项以输入服务器输出文件的访问路径和名称。

   >[!NOTE]
   >
   >始终在服务器上执行自动导入和导出作业。
   >
   >To export only some of the data, click **[!UICONTROL Advanced parameters]** and enter the number of lines to be exported in the appropriate field.

* 您可以创建差异导出以仅导出自上次执行后修改的记录。为此，请单击链 **[!UICONTROL Advanced parameters]** 接，然后单击选 **[!UICONTROL Differential export]** 项卡，然后选择 **[!UICONTROL Activate differential export]**。

   ![](assets/s_ncs_user_export_wizard02_b.png)

   您必须输入上次修改的日期。它可以从字段中检索或计算。

### 第 3 步 - 定义输出格式 {#step-3---defining-the-output-format}

选择导出文件的输出格式。可以使用以下格式：文本、固定列文本、CSV 和 XML。

![](assets/s_ncs_user_export_wizard03.png)

* For **[!UICONTROL Text]** format, select the delimiters to separate the columns (tabs, commas, semi-colons, or custom) and the strings (single or double quotes, or none).
* 对于 **[!UICONTROL text]** 和 **[!UICONTROL CSV]**，您可以选择选项 **[!UICONTROL Use first lines as column titles]**。
* 指示日期格式和数字格式。To do this, click the **[!UICONTROL Edit]** button for the field concerned and use the editor.
* 对于包含枚举值的字段，可以选 **[!UICONTROL Export labels instead of internal values of enumerations]**&#x200B;择。 For example, the title can be stored in the form **1=Mr.**, **2=Miss**, **3=Mrs.**. 如果选择此选项，将导出 **Mr.****、Miss** 和 **Mrs.**。

### 第 4 步 - 数据选择 {#step-4---data-selection}

选择要导出的字段。操作步骤：

1. Double-click the desired fields in the **[!UICONTROL Available fields]** list in order to add them to the **[!UICONTROL Output columns]** section.
1. 使用清单右侧的箭头定义输出文件中字段的顺序。

   ![](assets/s_ncs_user_export_wizard04.png)

1. Click the **[!UICONTROL Add]** button to call on functions. 有关此的详细信息，请参 [阅函数列表](../../platform/using/defining-filter-conditions.md#list-of-functions)。

### 第 5 步 - 对列进行排序 {#step-5---sorting-columns}

选择列的排序顺序。

![](assets/s_ncs_user_export_wizard05.png)

### 第 6 步 - 筛选条件 {#step-6---filter-conditions-}

您可以添加筛选条件以避免导出所有数据。此筛选的配置与投放向导中的收件人定位相同。请参见[此页面](../../delivery/using/steps-defining-the-target-population.md)。

![](assets/s_ncs_user_export_wizard05_b.png)

### 第 7 步 – 设定数据格式 {#step-7---data-formatting}

您可以修改输出文件的字段顺序和标签，并将转换应用于源数据。

* 要更改要导出的列的顺序，请选择相关列，然后使用表右侧的蓝色箭头。
* To change the label of a field, click in the cell of the **[!UICONTROL Label]** column that matches the field to be modified, and enter the new label. 按键盘上的 Enter 确认。
* To apply a case transformation to the content of a field, select it from the **[!UICONTROL Transformation]** column. 您可以选择：

   * 切换到小写
   * 切换到大写
   * 首字母大写

   ![](assets/s_ncs_user_export_wizard06.png)

* Click **[!UICONTROL Add a calculated field]** if you want to create a new calculated field (for example, a column containing last name + first name). For more on this, refer to [Calculated fields](../../platform/using/importing-data.md#calculated-fields).

如果要导出元素集合（例如，收件人的订阅，它们所属的清单等），则必须指定要导出的集合中的元素数量。

![](assets/s_ncs_user_export_wizard06_c.png)

### 第 8 步 - 数据预览 {#step-8---data-preview}

单 **[!UICONTROL Start the preview of the data]** 击以预览导出结果。 按照默认，显示前 200 行。To change this value, click the arrows to the right of the **[!UICONTROL Lines to display]** field.

![](assets/s_ncs_user_export_wizard07.png)

点击向导底部的选项卡，从列中结果的预览切换到 XML 中的结果。您还可以查看生成的 SQL 查询。

### 第 9 步 - 启动导出 {#step-9---launching-the-export}

单击 **[!UICONTROL Start]** 启动数据导出。

![](assets/s_ncs_user_export_wizard08.png)

## 通过工作流程导出数据 {#exporting-data-via-a-workflow}

在使用可用于转换数据的一些可用数据管理活动之后，可以使用工作流程来自动执行某些导出过程或导出精确数据集。

要了解有关从工作流程导出数据的更多信息，请参见[此部分](../../workflow/using/how-to-use-workflow-data.md)。
