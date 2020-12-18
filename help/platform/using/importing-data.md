---
solution: Campaign Classic
product: campaign
title: 导入数据
description: 导入数据
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '4136'
ht-degree: 64%

---


# 导入数据{#importing-data}

Adobe Campaign 允许您以文本、CSV、TAB 或 XML 格式从一个或多个文件将数据导入数据库。这些文件与表（主表或链接的表）相关联，并且源文件的每个字段与数据库的字段相关联。可以保存导入配置以便重复使用，让您可以计划导入任务以自动执行复制操作。

>[!NOTE]
>
>您无需使用&#x200B;**[!UICONTROL Import a list]**&#x200B;函数将数据与数据库数据映射即可导入数据。
>
>然后，可以通过&#x200B;**[!UICONTROL Read list]**&#x200B;对象在工作流中专门使用数据。 有关详细信息，请参见[此页面](../../workflow/using/read-list.md)。

![](assets/do-not-localize/how-to-video.png) [在视频中发现此功能](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/profile-management/importing-profiles.html)

## 要导入的数据的结构 {#structure-of-the-data-to-import}

在源文件中，每行与一条记录重合。记录中的数据由分隔符（空格、制表符、字符等）分隔。这意味着以列的形式检索数据，并且每列与数据库的字段相关联。

## 导入向导 {#import-wizard}

导入向导允许您配置导入，定义其选项（例如数据转换）和启动执行。它是一系列屏幕，其内容取决于导入类型（简单或多个）和操作员权限。

>[!NOTE]
>
>如果使用 IIS Web 服务器，则可能需要通过配置授权上传大文件 (> 28 MB)。
>
>有关更多信息，请参见[此章节](../../installation/using/integration-into-a-web-server-for-windows.md#changing-the-upload-file-size-limit)。

### 第1步 - 选择导入模板 {#step-1---choosing-the-import-template}

启动导入向导时，首先必须选择模板。例如，要配置导入收到简报的收件人，请按照以下步骤操作：

1. 选择&#x200B;**[!UICONTROL Profiles and Targets > Job > Generic imports and exports]**&#x200B;文件夹。
1. 点击 **New**，然后点击 **Import** 以创建导入模板。

   ![](assets/s_ncs_user_import_wizard01_1.png)

1. 单击&#x200B;**[!UICONTROL Import template]**&#x200B;字段右侧的箭头以选择模板，或单击&#x200B;**[!UICONTROL Select link]**&#x200B;以浏览树。

   本机模板为&#x200B;**[!UICONTROL New text import]**。 不得修改此模板，但您可以根据您的要求复制它以配置新模板。默认情况下，导入模板保存在&#x200B;**[!UICONTROL Profiles and targets > Templates > Job templates]**&#x200B;节点中。

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;字段中输入此导入的名称。 您可以添加描述。
1. 在相应字段中选择导入类型。导入有两种可能类型：**[!UICONTROL Simple import]**&#x200B;仅导入一个文件，**[!UICONTROL Multiple import]**&#x200B;在一次执行中导入多个文件。

   对于多次导入，请从导入向导的第一个屏幕的&#x200B;**[!UICONTROL Import type]**&#x200B;下拉列表中选择&#x200B;**[!UICONTROL Multiple import]**。

   ![](assets/s_ncs_user_import_wizard01_2.png)

1. 通过单击&#x200B;**[!UICONTROL Add]**&#x200B;指定要导入的字段。

   ![](assets/s_ncs_user_import_wizard01_3.png)

   每次添加文件时，都会显示&#x200B;**[!UICONTROL File to import]**&#x200B;向导的屏幕。 请参阅[步骤2 —— 源文件选择](#step-2---source-file-selection)部分，并按照向导中的步骤定义简单导入的导入选项。

   >[!NOTE]
   >
   >Multiple import 应仅用于满足特定需求，不是建议的选项。

#### 高级参数 {#advanced-parameters}

通过&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;链接可访问以下选项：

* **[!UICONTROL General]** 选项卡

   * **[!UICONTROL Stop execution if there are too many rejects]**

      默认选中此选项。如果要继续执行导入而不考虑拒绝次数，可以取消选择。默认情况下，如果拒绝前 100 行，则停止执行。

   * **[!UICONTROL Trace mode]**

      选择此选项可追踪每行的导入执行情况。

   * **[!UICONTROL Start the job in a detached process]**

      默认选中此选项。它允许您分离导入的执行，使其不会影响数据库中正在进行的其他作业。

   * **[!UICONTROL Do not update enumerations]**

      选择此选项可避免扩大数据库中的枚举值清单。请参阅[管理明细列表](../../platform/using/managing-enumerations.md)。

* **[!UICONTROL Variables]** 选项卡

   您可以定义与可在查询编辑器和计算字段中访问的作业关联的变量。要创建变量，请单击&#x200B;**[!UICONTROL Add]**&#x200B;并使用变量编辑器。

   >[!CAUTION]
   >
   >**[!UICONTROL Variables]**&#x200B;选项卡仅用于工作流类型编程，且应仅由专家用户配置。

### 第 2 步 - 源文件选择 {#step-2---source-file-selection}

源文件可以是文本格式（txt、csv、tab、固定列）或 xml。

默认情况下，**[!UICONTROL Upload file on the server]**&#x200B;处于选中状态。 单击&#x200B;**[!UICONTROL Local file]**&#x200B;字段右侧的文件夹，浏览本地磁盘并选择要导入的文件。 您可以取消选择此选项以输入访问路径以及要在服务器上导入的文件名。

![](assets/s_ncs_user_import_wizard02_1.png)

指定文件后，可单击&#x200B;**[!UICONTROL Auto-detect format]**&#x200B;在窗口的下半部分视图其数据。 此预览显示源文件的前 200 行。

![](assets/s_ncs_user_import_wizard02_2.png)

使用此视图上方提供的选项配置导入。通过这些选项定义的参数将传输到预览中。可以使用以下选项：

* **[!UICONTROL Click here to change the file format...]** 允许您检查文件格式并微调配置。
* **[!UICONTROL Update on server...]** 允许您将本地文件传输到服务器。仅当选择&#x200B;**[!UICONTROL Upload file on the server]**&#x200B;时，此选项才可用。
* **[!UICONTROL Download]** 仅当文件已上载到服务器上时才可用。
* **[!UICONTROL Auto-detect format]** 用于重新初始化数据源的格式。此选项允许您将原始格式重新应用于已通过&#x200B;**[!UICONTROL Click here to change the file format...]**&#x200B;选项格式化的数据。
* 通过&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;链接可过滤源数据并访问高级选项。 在此屏幕中，您可以选择仅导入部分文件。您还可以定义筛选器，例如，根据相应行的值仅导入“潜在客户”或“客户”类型的用户。这些选项仅供专业 JavaScript 用户使用。

#### 更改文件格式 {#changing-the-file-format}

使用&#x200B;**[!UICONTROL Click here to change the file format...]**&#x200B;选项可以格式化源文件的数据，特别是指定列分隔符和每个字段的数据类型。 此配置通过以下窗口执行：

![](assets/s_ncs_user_import_wizard02_3.png)

此步骤允许您描述应如何读取文件字段的值。例如，在日期的情况下，日期或日期+时间数据可以与某种格式（dd/mm/yyyy、mm/dd/yy 等）相关联。如果输入数据与预期格式不匹配，则在导入期间将发生拒绝。

您可以在窗口下部的预览区域中查看配置结果。

单击&#x200B;**[!UICONTROL OK]**&#x200B;以保存格式，然后单击&#x200B;**[!UICONTROL Next]**&#x200B;以显示下一步。

### 第 3 步 - 字段映射 {#step-3---field-mapping}

然后，您必须选择目标模式并将每列的数据映射到数据库中的字段。

![](assets/s_ncs_user_import_wizard03_1.png)

* 通过&#x200B;**[!UICONTROL Destination schema]**&#x200B;字段，可以选择要导入数据的模式。 此信息是强制性的。单击&#x200B;**[!UICONTROL Select link]**&#x200B;图标以选择现有模式之一。 单击&#x200B;**[!UICONTROL Edit link]**&#x200B;以显示所选表的内容。
* 中央表显示源文件中定义的所有字段。选择要导入的字段以将目标文件与它们相关联。可以手动或自动映射这些字段。

   要手动映射字段，请点击复选框以选择源字段，然后点击第二列以激活与所选字段映射的单元格。然后，单击&#x200B;**[!UICONTROL Edit expression]**&#x200B;图标以显示当前表的所有字段。 选择目标字段，然后单击&#x200B;**[!UICONTROL OK]**&#x200B;验证映射。

   要自动关联源字段和目标字段，请单击字段列表右侧的&#x200B;**[!UICONTROL Guess the destination fields]**&#x200B;图标。 如果需要，可以修改建议的字段。

   >[!CAUTION]
   >
   >在继续执行下一步之前，务必验证此操作的结果。

* 您可以将转换应用于导入的字段。为此，请单击与相关字段相关的&#x200B;**[!UICONTROL Transformation]**&#x200B;列的单元格，然后选择要应用的转换。

   ![](assets/s_ncs_user_import_wizard03_2.png)

   >[!CAUTION]
   >
   >转换在导入时应用。但是，如果已定义了对目标字段的约束（在上面的示例中为 @lastname 字段），则这些约束优先。

* 您可以使用位于中央表右侧的相应图标添加计算字段。通过计算字段，您可以执行复杂的转换，添加虚拟列或合并多列的数据。有关各种可能性的详细信息，请参见以下部分。

#### 计算字段 {#calculated-fields}

计算字段是添加到源文件并从其他列计算所得到的新列。然后，计算字段可以与 Adobe Campaign 数据库的字段相关联。但是，在计算字段中无法进行对帐操作。

有四种类型的计算字段：

* **[!UICONTROL Fixed string]**:对于源文件的所有行，计算字段的值都相同。允许您设置插入或更新的记录的字段值。例如，您可以为所有导入的记录将标记设置为“是”。
* **[!UICONTROL String with JavaScript tags]**:计算字段的值是包含JavaScript命令的字符串。
* **[!UICONTROL JavaScript expression]**:计算字段的值是评估JavaScript函数的结果。返回的值可以是数字、日期等。
* **[!UICONTROL Enumeration]**:根据源文件中包含的值将字段的值归因。编辑器允许您指定源列并输入枚举值清单，如以下示例所示：

   ![](assets/s_ncs_user_import_wizard03_3.png)

   使用&#x200B;**[!UICONTROL Preview]**&#x200B;选项卡可以视图定义的配置结果。 此处已添加&#x200B;**[!UICONTROL Subscription]**&#x200B;列。 该值通过 **Status** 字段计算。

   ![](assets/s_ncs_user_import_wizard03_4.png)

### 第 4 步 – 调解 {#step-4---reconciliation}

导入向导的调解步骤允许您定义将文件中的数据与数据库中的现有数据进行调解的模式，并设置文件数据和数据库数据之间的优先级规则。配置窗口如下所示：

![](assets/s_ncs_user_import_wizard04_1.png)

屏幕的中央部分包含一个树状结构，其中包含要导入数据的 Adobe Campaign 数据库的字段和表。

每个节点（表或字段）都有特殊选项。点击清单中的相关节点时，其参数和简要说明将显示在下方。为每个元素定义的行为显示在相应的&#x200B;**[!UICONTROL Behavior]**&#x200B;列中。

![](assets/s_ncs_user_import_wizard04_2.png)

#### 操作类型 {#types-of-operation}

对于与导入相关的每个表，都必须定义操作类型。以下操作可用于数据库的主要元素：

* **[!UICONTROL Update or insertion]**:如果记录存在于数据库中，则更新该记录，如果不存在，则创建该记录。
* **[!UICONTROL Insertion]**:将记录插入数据库。
* **[!UICONTROL Update]**:仅更新现有记录（忽略其他记录）。
* **[!UICONTROL Reconciliation only]**:在数据库中查找记录，但不执行更新。例如，允许您根据文件列关联要导入的收件人文件夹，而不更新文件夹中的数据。
* **[!UICONTROL Deletion]**:允许您销毁数据库中的记录。

导入所涉及的表中的每个字段都有以下选项：

* **[!UICONTROL Update (empty) if source value is empty]**:在更新事件中，如果源文件中的字段为空，则字段中的值将删除数据库值。否则，保留数据库字段。
* **[!UICONTROL Update only if destination is empty]**:除非数据库字段为空，否则源文件中的值不会覆盖数据库字段中的值。在这种情况下，它采用源文件的值。
* **[!UICONTROL Update the field only when the record is inserted]**:在更新或插入操作期间，将只导入新的源文件记录。

>[!NOTE]
>
>除非在没有重复数据删除的情况下插入，否则合并关键项的定义始终是&#x200B;**强制**&#x200B;的。

#### 合并关键项 {#reconciliation-keys}

必须至少填写一个合并关键项才能管理重复数据删除。

合并关键项是用于标识记录的一组字段。例如，要导入收件人，合并关键项可以是账号，“电子邮件”字段或“姓氏、名字、公司”字段等。

在这种情况下，要查明文件的某一行是否与数据库中的现有收件人匹配，导入引擎会将该文件的值与该键的所有字段的数据库值进行比较。当字段特定于记录时，可以执行源数据和目标数据之间的精细比较，从而保证导入后数据的完整性。可以为同一个表填写第二个合并关键项；它用于第一个关键项为空的行。

避免选择在导入期间可能被修改的字段；如果发生这种情况，引擎可能会创建额外的记录。

![](assets/s_ncs_user_import_wizard04_3.png)

>[!NOTE]
>
>对于收件人导入，所选文件夹的标识符将隐含地添加到密钥中。
>
>因此，仅对此文件夹执行调解（除非未选择任何文件夹）。

#### 重复数据删除 {#deduplication}

>[!NOTE]
>
>“double”是指在要导入的文件中存在两次或更多次的项目。
>
>“duplicate”是指同时存在于要导入的文件和数据库中的项目。

在&#x200B;**[!UICONTROL Management of doubles]**&#x200B;字段中可以配置外部重复数据删除。 重复数据删除涉及&#x200B;**源文件**&#x200B;中多次出现的记录（或多文件导入时的源文件），即合并关键项的字段相同的行。

* **[!UICONTROL Update]**&#x200B;模式（默认模式）中的重复管理不执行外部重复数据删除。 因此，最后一条记录具有优先权（因为它更新了先前记录的数据）。在此模式下不执行重复计数。
* 在&#x200B;**[!UICONTROL Ignore]**&#x200B;模式或&#x200B;**[!UICONTROL Reject entity]**&#x200B;中进行重复管理会排除导入中的重复。 在这种情况下，不会导入任何记录。
* 在&#x200B;**[!UICONTROL Reject entity]**&#x200B;模式中，不导入元素，并在导入日志中生成错误。
* 在&#x200B;**[!UICONTROL Ignore]**&#x200B;模式中，未导入元素，但未保留错误跟踪。 此模式可让您优化性能。

>[!CAUTION]
>
>重复数据删除仅在内存中执行。因此，采用重复数据删除的导入存在大小限制。限制取决于几个参数（应用程序服务器的容量、活动、密钥中的字段数等）。重复数据删除的最大大小为 1,000,000 行。

重复数据删除涉及源文件和数据库中都存在的记录。它只涉及更新操作(即&#x200B;**[!UICONTROL Update and insertion]**&#x200B;或&#x200B;**[!UICONTROL Update]**)。 使用&#x200B;**[!UICONTROL Duplicate management]**&#x200B;选项，可以更新或忽略记录（如果记录在源文件和数据库中）。 **[!UICONTROL Update or insert based on origin]**&#x200B;选项属于可选模块，不能用于标准上下文。

选项&#x200B;**[!UICONTROL Reject]**&#x200B;和&#x200B;**[!UICONTROL Ignore]**&#x200B;如上所示。

#### 发生错误时的行为 {#behavior-in-the-event-of-an-error}

大多数数据传输操作会产生各种类型的错误（不一致的行格式，无效的电子邮件地址等）。导入引擎生成的所有错误和所有警告都将存储并链接到导入实例。

![](assets/s_ncs_user_import_general_tab.png)

这些拒绝的详细信息可通过&#x200B;**[!UICONTROL Rejects]**&#x200B;选项卡查看。

![](assets/s_ncs_user_import_rejets_tab.png)

拒绝有两种类型（类型显示在&#x200B;**[!UICONTROL Connector]**&#x200B;列中）:

* 拒绝文本连接器涉及在处理文件行时发生的错误（计算字段、数据分析等）。在这种情况下，如果发生错误，则始终拒绝整行。
* 数据库连接器拒绝涉及数据调解或写入数据库期间发生的错误。在导入到多个表的情况下，拒绝只涉及记录的一部分（例如，对于收件人和相关事件的导入，错误可以阻止更新事件而不拒绝收件人）。

在数据调解页面中，您可以按字段和逐个表定义所需的错误管理类型字段。

* **[!UICONTROL Ignore and log a warning]**:除生成错误的字段外，所有字段都会导入到数据库。
* **[!UICONTROL Reject parent element]**:记录的整行将被拒绝，而不仅仅是导致错误的字段。
* **[!UICONTROL Reject all elements]**:导入停止，并拒绝记录的所有元素。

   ![](assets/s_ncs_user_import_wizard04_4.png)

导入实例的拒绝屏幕中的树状结构指示哪些字段被拒绝以及错误发生的位置。

可以通过&#x200B;**[!UICONTROL Export rejects]**&#x200B;图标生成包含这些记录的文件：

![](assets/s_ncs_user_import_errors_export.png)

### 第 5 步 - 导入收件人时的附加步骤 {#step-5---additional-step-when-importing-recipients}

导入向导的下一步允许您选择或创建将导入数据的文件夹，自动将导入的收件人映射到（新的或现有的）清单，将收件人订阅映射到服务。

![](assets/s_ncs_user_import_wizard05_1.png)

>[!NOTE]
>
>在仅导入收件人时以及使用预设的 Adobe Campaign 收件人表 (**nms:recipient**) 时，将出现此步骤。

* 单击&#x200B;**[!UICONTROL Edit]**&#x200B;链接以选择要关联或订阅列表的文件夹、收件人或服务。

   1. 导入到文件夹中

      通过&#x200B;**[!UICONTROL Import into a folder]**&#x200B;部分的&#x200B;**[!UICONTROL Edit...]**&#x200B;链接，可以选择或创建要将收件人导入到其中的文件夹。 默认情况下，如果未定义分区，则会将数据导入到操作员的预设文件夹中。

      >[!NOTE]
      >
      >操作员的预设文件夹是操作员具有写访问权限的第一个文件夹。请参阅[文件夹访问管理](../../platform/using/access-management.md#folder-access-management)。

      要选择导入文件夹，请单击&#x200B;**[!UICONTROL Folder]**&#x200B;字段右侧的箭头，然后选择相关文件夹。 还可以使用&#x200B;**[!UICONTROL Select link]**&#x200B;图标在新窗口中显示树或创建新文件夹。

      ![](assets/s_ncs_user_import_wizard05_2.png)

      要创建新文件夹，请选择要从中添加文件夹的节点，然后按鼠标右键。选择 **[!UICONTROL Create a new 'Recipients' folder]**。

      ![](assets/s_ncs_user_import_wizard05_3.png)

      该文件夹会添加到当前节点下方。输入新文件夹的名称，按Enter进行确认，然后单击&#x200B;**[!UICONTROL OK]**。

      ![](assets/s_ncs_user_import_wizard05_4.png)

   1. 与清单相关联

      通过&#x200B;**[!UICONTROL Add recipients to a list]**&#x200B;部分的&#x200B;**[!UICONTROL Edit...]**&#x200B;链接，可以选择或创建将收件人导入其中的列表。

      ![](assets/s_ncs_user_import_wizard05_5.png)

      您可以通过单击&#x200B;**[!UICONTROL Select link]**，然后单击&#x200B;**[!UICONTROL Create]**&#x200B;为这些列表创建新收件人。 创建和管理列表在[创建和管理列表](../../platform/using/creating-and-managing-lists.md)中介绍。

      ![](assets/s_ncs_user_import_wizard05_6.png)

      您可以决定将收件人添加到清单中已存在的收件人，或者使用新收件人重新创建清单。在这种情况下，如果清单已包含收件人，则它们将被删除并被导入的收件人替换。

   1. 订阅服务

      要将所有导入的收件人订阅到信息服务，请单击&#x200B;**[!UICONTROL Subscribe recipients to a service]**&#x200B;部分的&#x200B;**[!UICONTROL Edit...]**&#x200B;链接，以选择或创建收件人将订阅的信息服务。 您可以选择&#x200B;**[!UICONTROL Send a confirmation message]**&#x200B;选项：此消息的内容在与投放模板关联的订阅服务中定义。

      ![](assets/s_ncs_user_import_wizard05_7.png)

      您可以单击&#x200B;**[!UICONTROL Select link]**，然后单击&#x200B;**[!UICONTROL Create]**&#x200B;图标，为这些收件人创建新服务。 [这部分](../../delivery/using/managing-subscriptions.md)介绍了信息服务的管理。

* 使用&#x200B;**[!UICONTROL Origin]**&#x200B;字段向用户档案添加有关收件人来源的信息。 此信息在多次导入的框架内特别有用。

单击&#x200B;**[!UICONTROL Next]**&#x200B;验证此步骤并显示以下步骤。

### 第 6 步 - 启动导入 {#step-6---launching-the-import}

向导的最后一步允许您启动数据导入。为此，请单击&#x200B;**[!UICONTROL Start]**&#x200B;按钮。

![](assets/s_ncs_user_import_wizard06_1.png)

### 作业状态 {#job-statuses}

作业状态表示作业的当前状态。每个状态都由一个特殊的图标和标签表示。此信息显示在作业列表中。状态及其图标如下：

![](assets/s_ncs_user_export_status.png)

* **正在编辑**

   正在创建作业。

* **正在执行**

   此作业正在执行。

* **取消**

   单击&#x200B;**[!UICONTROL Cancel]**&#x200B;按钮：正在进行的作业已取消。

* **正在取消**

   取消命令已接收并且正在取消作业。

* **正在暂停**

   单击&#x200B;**[!UICONTROL Pause]**:工作正被暂停。

* **已暂停**

   单击&#x200B;**[!UICONTROL Pause]**:作业被暂停。 单击&#x200B;**[!UICONTROL Start]**&#x200B;可重新启动它。

* **已完成**

   作业的执行已完成。

* **已完成且存在错误**

   由于技术错误，该作业未执行。

* **正在关闭服务器**

   正在进行的作业因 Adobe Campaign 服务器已关闭而中断。

## 一般导入范例 {#generic-import-samples}

### 示例：从列表{#example--import-from-a-list-of-recipients}收件人导入

要从清单概述创建和提供收件人清单，请应用以下步骤：

1. 创建清单

   * 单击Adobe Campaign主页&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;菜单中的&#x200B;**[!UICONTROL Lists]**&#x200B;链接。
   * 单击&#x200B;**[!UICONTROL Create]**，然后单击&#x200B;**[!UICONTROL Import a list]**&#x200B;按钮。

1. 选择要导入的文件

   单击&#x200B;**[!UICONTROL Local file]**&#x200B;字段右侧的文件夹，然后选择包含要导入的列表的文件。

   ![](assets/s_ncs_user_import_example00_01.png)

1. 清单名称和存储

   输入列表的名称，然后选择应保存的目录。

   ![](assets/s_ncs_user_import_example00_02.png)

1. 启动导入

   单击&#x200B;**[!UICONTROL Next]**，然后单击&#x200B;**[!UICONTROL Start]**&#x200B;以开始导入列表。

   ![](assets/s_ncs_user_import_example00_03.png)

### 示例：从文本文件导入新记录 {#example--import-new-records-from-a-text-file-}

要将存储在文本文件中的新收件人配置文件导入 Adobe Campaign 数据库，请使用以下步骤：

1. 选择模板

   * 在Adobe Campaign主页中，单击&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;链接，然后单击&#x200B;**[!UICONTROL Jobs]**。 在作业列表上方，单击&#x200B;**[!UICONTROL New import]**。
   * 默认情况下，保持选中&#x200B;**[!UICONTROL New text import]**&#x200B;模板。
   * 更改标签和描述。
   * 选择 **[!UICONTROL Simple import]**。
   * 保留默认作业文件夹。
   * 单击&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;并选择&#x200B;**[!UICONTROL Tracking mode]**&#x200B;选项，以视图执行过程中导入的详细信息。

1. 选择要导入的文件

   单击&#x200B;**[!UICONTROL Local file]**&#x200B;字段右侧的文件夹，然后选择要导入的文件。

   ![](assets/s_ncs_user_import_example01_01.png)

1. 关联字段

   单击&#x200B;**[!UICONTROL Guess the destination fields]**&#x200B;图标自动映射源模式和目标数据。 单击&#x200B;**[!UICONTROL Next]**&#x200B;前，请检查此窗口中的信息。

   ![](assets/s_ncs_user_import_example03_01.png)

1. 协调

   * 转到 **Recipients (nms:recipient)** 表。
   * 选择&#x200B;**[!UICONTROL Insertion]**&#x200B;操作，并保留其他字段的默认值。

      ![](assets/s_ncs_user_import_example04_01.png)

1. 导入收件人

   * 如有必要，请为要导入的记录指定一个文件夹。

      ![](assets/s_ncs_user_import_example05_01.png)

1. 启动导入

   * 单击 **[!UICONTROL Start]**.

      在编辑器的中心区域，您可以检查导入操作是否成功并查看已处理的记录数。

      ![](assets/s_ncs_user_import_example06_01.png)

      通过&#x200B;**[!UICONTROL Tracking]**&#x200B;模式，可以跟踪源文件中每个记录的导入详细信息。 为此，请在主页中单击&#x200B;**[!UICONTROL Profiles and Targets]**，然后单击&#x200B;**[!UICONTROL Processes]**，选择相关导入，并查找&#x200B;**[!UICONTROL General]**、**[!UICONTROL Journal]**&#x200B;和&#x200B;**[!UICONTROL Rejects]**&#x200B;选项卡。

      * 检查导入进度

         ![](assets/s_ncs_user_import_example07_01.png)

      * 处理每条记录的查看

         ![](assets/s_ncs_user_import_example07_02.png)

### 示例：更新和插入收件人{#example--update-and-insert-recipients}

我们希望更新数据库中的现有记录，并从文本文件中创建新记录。以下是该过程的示例：

1. 选择模板

   重复上面示例 2 中描述的步骤。

1. 要导入的文件

   选择要导入的文件。

   在我们的示例中，文件第一行的概述显示该文件包含三个记录的更新和一个记录的创建。

   ![](assets/s_ncs_user_import_example02_02.png)

1. 关联字段

   执行上面示例 2 中的过程。

1. 协调

   * 默认情况下，保持&#x200B;**[!UICONTROL Update or insert]**&#x200B;处于选中状态。
   * 将选项&#x200B;**[!UICONTROL Management of duplicates]**&#x200B;保留在&#x200B;**[!UICONTROL Update]**&#x200B;模式中，以便使用文本文件中的数据修改数据库中的现有记录。
   * 选择字段&#x200B;**[!UICONTROL Birth date]**、**[!UICONTROL Name]**&#x200B;和&#x200B;**[!UICONTROL Company]**，并为它们分配合并关键项。

      ![](assets/s_ncs_user_import_example04_02.png)

1. 启动导入

   * 单击 **[!UICONTROL Start]**.

      在追踪窗口中，您可以检查导入是否成功并查看已处理的记录数。

      ![](assets/s_ncs_user_import_example06_02.png)

   * 查看收件人表以检查此操作已修改记录。

      ![](assets/s_ncs_user_import_example06_03.png)

### 示例：用外部文件{#example--enrich-the-values-with-those-of-an-external-file}的值进行扩充

我们希望通过文本文件修改数据库表中的某些字段，且优先考虑数据库中包含的值。

在此示例中，您可以看到文本文件中的某些字段具有值，而数据库中的相应字段为空。其他字段包含与数据库中包含的值不同的值。

* 要导入的文本文件的内容。

   ![](assets/s_ncs_user_import_example02_03.png)

* 导入前的数据库状态

   ![](assets/s_ncs_user_import_example06_04.png)

应用以下步骤：

1. 选择模板

   执行上面示例 2 中的过程。

1. 要导入的文件

   选择要导入的文件。

1. 关联字段

   执行上面示例 2 中的过程。

   在预览文件的第一行时，您可以看到该文件包含某些记录的更新。

1. 协调

   * 转到表并选择&#x200B;**[!UICONTROL Update]**&#x200B;操作。
   * 为&#x200B;**[!UICONTROL Management of doubles]**&#x200B;字段选择选项&#x200B;**[!UICONTROL Reject entity]**。
   * 将选项&#x200B;**[!UICONTROL Management of duplicates]**&#x200B;保留在&#x200B;**[!UICONTROL Update]**&#x200B;模式中，以便使用文本文件中的数据修改数据库中的现有记录。
   * 将光标放在&#x200B;**[!UICONTROL Last name (@lastName)]**&#x200B;节点上，然后选择&#x200B;**[!UICONTROL Update only if destination is empty]**&#x200B;选项。
   * 对&#x200B;**[!UICONTROL Company (@company)]**&#x200B;节点重复此操作。
   * 为字段&#x200B;**[!UICONTROL Birth date]**、**[!UICONTROL E-mail]**&#x200B;和&#x200B;**[!UICONTROL First name]**&#x200B;分配合并关键项。

      ![](assets/s_ncs_user_import_example04_03.png)

1. 启动导入

   单击 **[!UICONTROL Start]**.

   查看收件人表以确认导入已修改记录。

   ![](assets/s_ncs_user_import_example06_05.png)

   只有空值被文本文件中的值替换，但数据库中的现有值未被导入文件中的值覆写。

### 示例：更新并扩充外部文件{#example--update-and-enrich-the-values-from-those-in-an-external-file}中的值

我们希望使用文本文件修改数据库表中的某些字段，优先套用文本文件中包含的值。

在此示例中，您将看到文本文件中的某些字段具有空值，而数据库中的相应字段不为空。其他字段包含与数据库中的值不同的值。

* 要导入的文本文件的内容。

   ![](assets/s_ncs_user_import_example02_04.png)

* 导入前的数据库状态

   ![](assets/s_ncs_user_import_example06_07.png)

1. 选择模板

   执行上面示例 2 中的过程。

1. 要导入的文件

   选择要导入的文件。

   在预览文件的第一行时，您可以看到该文件包含空字段和某些记录的更新。

1. 关联字段

   执行上面示例 2 中的过程。

1. 协调

   * 转到表并选择&#x200B;**[!UICONTROL Update]**。
   * 为&#x200B;**[!UICONTROL Management of doubles]**&#x200B;字段选择选项&#x200B;**[!UICONTROL Reject entity]**。
   * 将选项&#x200B;**[!UICONTROL Management of duplicates]**&#x200B;保留为&#x200B;**[!UICONTROL Update]**&#x200B;模式，以使用文本文件中的数据修改数据库中的现有记录。
   * 将光标放在&#x200B;**[!UICONTROL Account number (@account)]**&#x200B;节点上，然后选择选项&#x200B;**[!UICONTROL Take empty values into account]**。
   * 选择字段&#x200B;**[!UICONTROL Birth date]**、**[!UICONTROL E-mail]**&#x200B;和&#x200B;**[!UICONTROL First name]**，并为它们分配合并关键项。

      ![](assets/s_ncs_user_import_example04_04.png)

1. 启动导入

   * 单击 **[!UICONTROL Start]**.
   * 查看收件人表以检查操作已修改的记录。

      ![](assets/s_ncs_user_import_example06_06.png)

      空文本文件的值已覆写数据库中的值。数据库中的现有值已更新为导入文件中的值，与步骤4中为重复选择的&#x200B;**[!UICONTROL Update]**&#x200B;选项保持一致。

## 从工作流程导入数据 {#importing-data-from-a-workflow}

工作流程可以用来自动执行某些导入过程。无论是从本地文件还是从 SFTP 导入数据，都可以使用工作流程来标准化数据管理过程。

要了解有关从工作流程导入数据的更多信息，请参见[此部分](../../workflow/using/importing-data.md)。
