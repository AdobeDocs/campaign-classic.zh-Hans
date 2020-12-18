---
solution: Campaign Classic
product: campaign
title: 导出数据
description: 导出数据
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 59%

---


# 导出数据{#exporting-data}

## 导出向导 {#export-wizard}

导出参数通过向导记录。通用导出模块作为标准提供，允许您从数据库存取和提取数据：联系人、客户、清单、细分等。例如，在电子表格中使用广告系列追踪数据（追踪历史记录等）非常有用。输出数据可以是 txt、CSV、TAB 或 XML 格式。

### 第 1 步 - 选择导出模板 {#step-1---choosing-the-export-template}

启动导出向导时，首先必须选择模板。例如，要配置最近注册的收件人的导出，请按照以下步骤操作：

1. 选择&#x200B;**[!UICONTROL Profiles and Targets > Job > Generic imports and exports]**&#x200B;文件夹。
1. 点击 **New**，然后点击 **Export** 以创建导出模板。

   ![](assets/s_ncs_user_export_wizard01.png)

1. 单击&#x200B;**[!UICONTROL Export template]**&#x200B;字段右侧的箭头以选择模板，或单击&#x200B;**[!UICONTROL Select link]**&#x200B;以浏览树。

   本机模板为&#x200B;**[!UICONTROL New text export]**。 不得修改此模板，但您可以复制它以配置新模板。默认情况下，导出模板保存在&#x200B;**[!UICONTROL Resources > Templates > Job templates]**&#x200B;节点中。

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;字段中输入要导出的名称。 您可以添加描述。
1. 选择导出类型。有两种可能的导出类型：**[!UICONTROL Simple export]**&#x200B;仅导出一个文件，**[!UICONTROL Multiple export]**&#x200B;在单次执行中从一个或多个类型的源文档导出多个文件。

### 第 2 步 - 要导出的文件类型 {#step-2---type-of-file-to-export}

选择要导出的文档类型，即要导出的数据模式。

默认情况下，从&#x200B;**[!UICONTROL Jobs]**&#x200B;节点启动导出时，数据将来自收件人表。 从列表数据（从&#x200B;**[!UICONTROL right click > Export]**&#x200B;菜单）启动导出时，数据所属的表会自动填入&#x200B;**[!UICONTROL Document type]**&#x200B;字段。

![](assets/s_ncs_user_export_wizard02.png)

* 默认情况下，**[!UICONTROL Download the file generated on the server after the export]**&#x200B;选项处于选中状态。 在&#x200B;**[!UICONTROL Local file]**&#x200B;字段中，填写要创建的文件的名称和路径，或通过单击字段右侧的文件夹浏览本地磁盘。 您可以取消选择此选项以输入服务器输出文件的访问路径和名称。

   >[!NOTE]
   >
   >始终在服务器上执行自动导入和导出作业。
   >
   >要仅导出部分数据，请单击&#x200B;**[!UICONTROL Advanced parameters]**，然后在相应字段中输入要导出的行数。

* 您可以创建差异导出以仅导出自上次执行后修改的记录。为此，请单击&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Differential export]**&#x200B;选项卡，然后选择&#x200B;**[!UICONTROL Activate differential export]**。

   ![](assets/s_ncs_user_export_wizard02_b.png)

   您必须输入上次修改的日期。它可以从字段中检索或计算。

### 第 3 步 - 定义输出格式 {#step-3---defining-the-output-format}

选择导出文件的输出格式。可以使用以下格式：文本、固定列文本、CSV 和 XML。

![](assets/s_ncs_user_export_wizard03.png)

* 对于&#x200B;**[!UICONTROL Text]**&#x200B;格式，选择分隔符以分隔各列（制表符、逗号、分号或自定义）和字符串(单引号或多次引号，或无)。
* 对于&#x200B;**[!UICONTROL text]**&#x200B;和&#x200B;**[!UICONTROL CSV]**，您可以选择选项&#x200B;**[!UICONTROL Use first lines as column titles]**。
* 指示日期格式和数字格式。要执行此操作，请单击相关字段的&#x200B;**[!UICONTROL Edit]**&#x200B;按钮，然后使用编辑器。
* 对于包含枚举值的字段，可以选择&#x200B;**[!UICONTROL Export labels instead of internal values of enumerations]**。 例如，标题可以以&#x200B;**1=Mr**、**2=Miss**、**3=Mrs的形式存储。**.如果选择此选项，将导出 **Mr.****、Miss** 和 **Mrs.**。

### 第 4 步 - 数据选择 {#step-4---data-selection}

选择要导出的字段。操作步骤：

1. 多次-单击&#x200B;**[!UICONTROL Available fields]**&#x200B;列表中的所需字段，以将其添加到&#x200B;**[!UICONTROL Output columns]**&#x200B;部分。
1. 使用清单右侧的箭头定义输出文件中字段的顺序。

   ![](assets/s_ncs_user_export_wizard04.png)

1. 单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以调用函数。 有关详细信息，请参阅[函数列表](../../platform/using/defining-filter-conditions.md#list-of-functions)。

### 第 5 步 - 对列进行排序 {#step-5---sorting-columns}

选择列的排序顺序。

![](assets/s_ncs_user_export_wizard05.png)

### 第 6 步 - 筛选条件 {#step-6---filter-conditions-}

您可以添加筛选条件以避免导出所有数据。此筛选的配置与投放向导中的收件人定位相同。请参见[此页面](../../delivery/using/steps-defining-the-target-population.md)。

![](assets/s_ncs_user_export_wizard05_b.png)

### 第 7 步 – 设定数据格式 {#step-7---data-formatting}

您可以修改输出文件的字段顺序和标签，并将转换应用于源数据。

* 要更改要导出的列的顺序，请选择相关列，然后使用表右侧的蓝色箭头。
* 要更改字段的标签，请单击与要修改的字段相匹配的&#x200B;**[!UICONTROL Label]**&#x200B;列的单元格，然后输入新标签。 按键盘上的 Enter 确认。
* 要将大小写转换应用于字段的内容，请从&#x200B;**[!UICONTROL Transformation]**&#x200B;列中选择它。 您可以选择：

   * 切换到小写
   * 切换到大写
   * 首字母大写

   ![](assets/s_ncs_user_export_wizard06.png)

* 如果要创建新的计算字段（例如，包含姓氏+名字的列），请单击&#x200B;**[!UICONTROL Add a calculated field]**。 有关详细信息，请参阅[计算字段](../../platform/using/importing-data.md#calculated-fields)。

如果要导出元素集合（例如，收件人的订阅，它们所属的清单等），则必须指定要导出的集合中的元素数量。

![](assets/s_ncs_user_export_wizard06_c.png)

### 第 8 步 - 数据预览 {#step-8---data-preview}

单击&#x200B;**[!UICONTROL Start the preview of the data]**&#x200B;以预览导出结果。 按照默认，显示前 200 行。要更改此值，请单击&#x200B;**[!UICONTROL Lines to display]**&#x200B;字段右侧的箭头。

![](assets/s_ncs_user_export_wizard07.png)

点击向导底部的选项卡，从列中结果的预览切换到 XML 中的结果。您还可以查看生成的 SQL 查询。

### 第 9 步 - 启动导出 {#step-9---launching-the-export}

单击&#x200B;**[!UICONTROL Start]**&#x200B;启动数据导出。

![](assets/s_ncs_user_export_wizard08.png)

## 通过工作流程导出数据 {#exporting-data-via-a-workflow}

在使用可用于转换数据的一些可用数据管理活动之后，可以使用工作流程来自动执行某些导出过程或导出精确数据集。

要了解有关从工作流程导出数据的更多信息，请参见[此部分](../../workflow/using/how-to-use-workflow-data.md)。
