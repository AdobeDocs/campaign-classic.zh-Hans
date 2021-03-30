---
solution: Campaign Classic
product: campaign
title: 使用数据包
description: 使用数据包
audience: platform
content-type: reference
topic-tags: administration-basics
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '2442'
ht-degree: 2%

---


# 使用数据包{#working-with-data-packages}

## 关于数据包{#about-data-packages}

使用 Adobe Campaign，您可以通过数据包系统导出或导入平台配置和数据。包可以包含不同类型的配置、元素，也可以过滤或不过滤。

数据包支持以 XML 格式文件的形式显示 Adobe Campaign 数据库的实体。数据包中包含的每个实体由其全部数据表示。

**数据包**&#x200B;的原理是导出数据配置并将其集成到另一个Adobe Campaign系统中。 了解如何在此[部分](#data-package-best-practices)中保持一组一致的数据包。

### 包{#types-of-packages}的类型

可导出包有三种类型：用户包、平台包和管理包。

* **用户包**:它允许您选择要导出的图元的列表。此类包管理依赖关系并验证错误。
* **平台包**:它包括所有附加的技术资源（非标准）：模式、JavaScript代码等。

   ![](assets/ncs_datapackage_package_platform.png)

* **管理包**:它包括所有添加的模板和业务对象（非标准）：模板、库等

   ![](assets/ncs_datapackage_package_admin.png)

>[!CAUTION]
>
>**platform**&#x200B;和&#x200B;**admin**&#x200B;类型包含要导出的实体的预定义列表。 每个实体都链接到过滤条件，这些条件允许您删除创建的包的现成资源。

## 数据结构{#data-structure}

数据包的描述是符合&#x200B;**xrk:navtree**&#x200B;文档模式语法的结构化XML。

数据包示例：

```
<package>
  <entities schema="nms:recipient">
    <recipient email="john.smith@adobe.com" lastName="Smith" firstName="John">      
      <folder _operation="none" name="nmsRootFolder"/>      
      <company _operation="none" name="Adobe"/>
    </recipient>
  </entities>
  <entities schema="sfa:company">
    <company name="Adobe">
      location city="London" zipCode="W11 2BQ"/>
    </company>
  </entities>
</package>
```

XML文档必须以&#x200B;**`<package>`**&#x200B;元素开头和结尾。 随后的任何&#x200B;**`<entities>`**&#x200B;元素按文档类型分发数据。

**`<entities>`**&#x200B;元素包含以在&#x200B;**模式**&#x200B;属性中输入的模式格式的包数据。

包中的数据不能包含基之间不兼容的内部密钥，如自动生成的密钥（**autopk**&#x200B;选项）。

在我们的示例中，“folder”和“公司”链接上的连接已替换为目标表上的所谓“高级”键：

```
<recipient>
  <folder _operation="none" name="nmsRootFolder"/>
  <company _operation="none" name="Adobe"/>
</recipient>
```

值为“none”的&#x200B;**`operation`**&#x200B;属性定义一个协调链接。

数据包可以从任何文本编辑器手动构建。 只需确保XML文档的结构符合“xtk:navtree”模式。 Adobe Campaign控制台具有数据包导出和导入模块。

## 导出包{#exporting-packages}

### 关于包导出{#about-package-export}

可以通过三种不同的方式导出包：

* **[!UICONTROL Package Export Wizard]**&#x200B;允许您导出单个包中的一组对象。 有关详细信息，请参阅[导出包](#exporting-a-set-of-objects-in-a-package)中的一组对象
* 通过右键单击&#x200B;**[!UICONTROL Actions > Export in a package]**&#x200B;并选择，可以直接在包中导出&#x200B;**单个对象**。
* **包定** 义允许您创建包结构，在其中可以添加稍后将在包中导出的对象。有关详细信息，请参阅[管理包定义](#managing-package-definitions)

导出包后，您将能够将它和所有添加的实体导入另一个活动实例。

### 导出包{#exporting-a-set-of-objects-in-a-package}中的一组对象

包导出向导可通过Adobe Campaign客户端控制台的&#x200B;**[!UICONTROL Tools > Advanced > Export package...]**&#x200B;菜单访问。

![](assets/ncs_datapackage_typepackage.png)

对于三种类型的包，向导将优惠以下步骤：

1. 列表要按文档类型导出的图元：

   ![](assets/ncs_datapackage_export2.png)

   >[!CAUTION]
   >
   >如果导出&#x200B;**[!UICONTROL Offer category]**、**[!UICONTROL Offer environment]**、**[!UICONTROL Program]**&#x200B;或&#x200B;**[!UICONTROL Plan]**&#x200B;类型文件夹，请不要选择&#x200B;**xtk:folder**，因为您可能会丢失一些数据。 选择与文件夹对应的实体：**nms:offerCategory**(对于优惠类别)、**nms:offerEnv**(对于优惠环境)、**nms:项目**(对于项目)和&#x200B;**nms:plan**（对于计划）。

   列表管理允许您添加或删除要从配置中导出的实体。 单击&#x200B;**[!UICONTROL Add]**&#x200B;以选择新实体。

   **[!UICONTROL Detail]**&#x200B;按钮编辑所选配置。

   >[!NOTE]
   >
   >依赖关系机制控制实体导出序列。 有关详细信息，请参阅[管理依赖项](#managing-dependencies)。

1. 实体配置屏幕定义要提取的文档类型的过滤器查询。

   必须为数据提取配置filtering子句。

   ![](assets/ncs_datapackage_export4.png)

   >[!NOTE]
   >
   >查询编辑器显示在[本节](../../platform/using/about-queries-in-campaign.md)中。

1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;并选择排序列以在提取期间对数据排序：

   ![](assets/ncs_datapackage_export5.png)

1. 预览要提取的数据，然后运行导出。

   ![](assets/ncs_datapackage_export6.png)

1. 包导出向导的最后一页可让您开始导出。 数据将存储在&#x200B;**[!UICONTROL File]**&#x200B;字段中指示的文件中。

   ![](assets/ncs_datapackage_export7.png)

### 管理依赖项{#managing-dependencies}

导出机制使Adobe Campaign能够跟踪各种导出元素之间的链接。

此机制由两个规则定义：

* 链接到具有&#x200B;**own**&#x200B;或&#x200B;**owncopy**&#x200B;类型完整性的链接的对象将导出到与导出对象相同的包中。
* 链接到具有&#x200B;**netural**&#x200B;或&#x200B;**define**&#x200B;类型完整性（已定义链接）的链接的对象必须单独导出。

>[!NOTE]
>
>链接到模式元素的完整性类型在[本节](../../configuration/using/database-mapping.md#links--relation-between-tables)中定义。

#### 导出活动{#exporting-a-campaign}

下面是如何导出活动的示例。 要导出的营销活动包含任务(标签：“MyTask”)和工作流(标签：“MyWorkflow”文件夹(节点：管理/生产/技术工作流/活动流程/ MyWorkflow)。

任务和工作流将导出到与活动相同的包中，因为匹配模式通过具有“自己”类型完整性的链接连接。

包内容：

```
<?xml version='1.0'?>
<package author="Administrator (admin)" buildNumber="7974" buildVersion="6.1" img=""
label="" name="" namespace="" vendor="">
 <desc></desc>
 <version buildDate="2013-01-09 10:30:18.954Z"/>
 <entities schema="nms:operation">
  <operation duration="432000" end="2013-01-14" internalName="OP1" label="MyCampaign"
  modelName="opEmpty" start="2013-01-09">
   <controlGroup>
    <where filteringSchema=""/>
   </controlGroup>
   <seedList>
    <where filteringSchema="nms:seedMember"></where>
    <seedMember internalName="SDM1"></seedMember>
   </seedList>
   <parameter useAsset="1" useBudget="1" useControlGroup="1" useDeliveryOutline="1"
   useDocument="1" useFCPValidation="0" useSeedMember="1" useTask="1"
   useValidation="1" useWorkflow="1"></parameter>
   <fcpSeed>
    <where filteringSchema="nms:seedMember"></where>
   </fcpSeed>
   <owner _operation="none" name="admin" type="0"/>
   <program _operation="none" name="nmsOperations"/>
   <task end="2013-01-17 10:07:51.000Z" label="MyTask" name="TSK2" start="2013-01-16 10:07:51.000Z"
   status="1">
    <owner _operation="none" name="admin" type="0"/>
    <operation _operation="none" internalName="OP1"/>
    <folder _operation="none" name="nmsTask"/>
   </task>
   <workflow internalName="WKF12" label="CampaignWorkflow" modelName="newOpEmpty"
   order="8982" scenario-cs="Notification of the workflow supervisor (notifySupervisor)"
   schema="nms:recipient">
    <scenario internalName="notifySupervisor"/>
    <desc></desc>
    <folder _operation="none" name="Folder4"/>
    <operation _operation="none" internalName="OP1"/>
   </workflow>
  </operation>
 </entities>
</package>   
```

在具有&#x200B;**和@pkgPlatform**&#x200B;属性的模式中定义与包类型的从属关系。 这两个属性都接收一个XTK表达式，它定义与包的从属关系条件。

```
<element name="offerEnv" img="nms:offerEnv.png" 
template="xtk:folder" pkgAdmin="@id != 0">
```

最后，**@pkgStatus**&#x200B;属性允许您为这些元素或属性定义导出规则。 根据属性的值，元素或属性将在导出的包中找到。 此属性的三个可能值是：

* **never**:不导出字段/链接
* **always**:向这个领域出口
* **preCreate**:授权创建链接实体

>[!NOTE]
>
>**preCreate**&#x200B;值仅允许链接类型事件。 它授权您创建或指向尚未加载到导出包中的实体。

## 管理包定义{#managing-package-definitions}

包定义允许您创建包结构，在其中可添加稍后将在单个包中导出的实体。 然后，您将能够将此包和所有添加的实体导入到另一个活动实例中。

**相关主题：**

* [创建包定义](#creating-a-package-definition)
* [将实体添加到包定义](#adding-entities-to-a-package-definition)
* [配置包定义生成](#configuring-package-definitions-generation)
* [从包定义导出包](#exporting-packages-from-a-package-definition)

### 创建包定义{#creating-a-package-definition}

可以从&#x200B;**[!UICONTROL Administration > Configuration > Package management > Package definitions]**&#x200B;菜单访问包定义。

要创建包定义，请单击&#x200B;**[!UICONTROL New]**&#x200B;按钮，然后填写包定义一般信息。

![](assets/packagedefinition_create.png)

然后，可以向包定义中添加实体，并将其导出到XML文件包。

**相关主题：**

* [将实体添加到包定义](#adding-entities-to-a-package-definition)
* [配置包定义生成](#configuring-package-definitions-generation)
* [从包定义导出包](#exporting-packages-from-a-package-definition)

### 将实体添加到包定义{#adding-entities-to-a-package-definition}

在&#x200B;**[!UICONTROL Content]**&#x200B;选项卡中，单击&#x200B;**[!UICONTROL Add]**&#x200B;按钮以选择要与包一起导出的实体。 选择实体时的最佳实践在[本节](#exporting-a-set-of-objects-in-a-package)部分中介绍。

![](assets/packagedefinition_addentities.png)

可以直接从实体在实例中的位置将实体添加到包定义。 为此请执行以下操作步骤：

1. 右键单击所需的实体，然后选择&#x200B;**[!UICONTROL Actions > Export in a package]**。

   ![](assets/packagedefinition_singleentity.png)

1. 选择&#x200B;**[!UICONTROL Add to a package definition]**，然后选择要向其添加实体的包定义。

   ![](assets/packagedefinition_packageselection.png)

1. 实体将添加到包定义中，它将随包一起导出（请参阅[此部分](#exporting-packages-from-a-package-definition)）。

   ![](assets/packagedefinition_entityadded.png)

### 配置包定义生成{#configuring-package-definitions-generation}

可以从包定义&#x200B;**[!UICONTROL Content]**&#x200B;选项卡中配置包生成。 为此，请单击&#x200B;**[!UICONTROL Generation parameters]**&#x200B;链接。

![](assets/packagedefinition_generationparameters.png)

* **[!UICONTROL Include the definition]**:包括当前在包定义中使用的定义。
* **[!UICONTROL Include an installation script]**:允许您添加要在包导入时执行的javascript脚本。选中后，**[!UICONTROL Script]**&#x200B;选项卡会添加到包定义屏幕中。
* **[!UICONTROL Include default values]**:向包中添加所有实体属性的值。

   为避免冗长的出口，默认情况下不选择此选项。 这意味着具有默认值(“空字符串”、“0”和“false”(如果未在模式中另行定义)的实体属性不会添加到包中，因此不会导出。

   >[!CAUTION]
   >
   >取消选择此选项可能会导致合并本地版本和导入的版本。
   >
   >如果导入包的实例包含与包的实体相同的实体（例如，具有相同的外部ID），则不会更新其属性。 如果前一个实例的属性具有默认值，则会发生这种情况，因为这些属性未包含在包中。
   >
   >在这种情况下，选择&#x200B;**[!UICONTROL Include default values]**&#x200B;选项将阻止版本合并，因为将随包一起导出前实例的所有属性。

### 从包定义{#exporting-packages-from-a-package-definition}导出包

要从包定义中导出包，请执行以下步骤：

1. 选择要导出的包定义，然后单击&#x200B;**[!UICONTROL Actions]**&#x200B;按钮并选择&#x200B;**[!UICONTROL Export the package]**。
1. 默认情况下，将选择与导出的包对应的XML文件。 它根据包定义命名空间和名称命名。
1. 定义包名称和位置后，单击&#x200B;**[!UICONTROL Start]**&#x200B;按钮启动导出。

   ![](assets/packagedefinition_packageexport.png)

## 导入包{#importing-packages}

包导入向导可通过Adobe Campaign客户端控制台的主菜单&#x200B;**[!UICONTROL Tools > Advanced > Package import...]**&#x200B;访问。

您可以从以前执行的导出(例如，从其他Adobe Campaign实例或[内置包](../../installation/using/installing-campaign-standard-packages.md))导入包，具体取决于许可证的条款。

![](assets/ncs_datapackage_import.png)

### 从文件{#installing-a-package-from-a-file}安装包

要导入现有数据包，请选择XML文件，然后单击&#x200B;**[!UICONTROL Open]**。

![](assets/ncs_datapackage_import_1.png)

随后，要导入的包的内容将显示在编辑器的中间部分。

单击&#x200B;**[!UICONTROL Next]**&#x200B;和&#x200B;**[!UICONTROL Start]**&#x200B;启动导入。

![](assets/ncs_datapackage_import_2.png)

### 安装内置包{#installing-a-standard-package}

标准包是内置包，在配置Adobe Campaign时安装。 根据您的权限和部署模式，如果您获得了新选项或加载项，或者升级到新优惠，则可以导入新的标准包。

请参阅您的许可协议以检查可以安装哪些包。

有关内置软件包的详细信息，请参阅[此页](../../installation/using/installing-campaign-standard-packages.md)。

## 数据包最佳实践{#data-package-best-practices}

本节介绍如何在项目的整个生命周期中以一致的方式组织数据包。

包可以包含不同类型的配置和元素，无论是否已过滤。 如果缺少某些元素或未按正确的顺序导入元素/包，平台配置可能会中断。

另外，由于多人在同一平台上工作，具有许多不同的功能，包规范文件夹会很快变得复杂。

虽然不是强制要求这样做，但本节优惠了一个解决方案，以帮助在Adobe Campaign中组织和使用适用于大型项目的包。

主要制约因素如下：
* 整理包并跟踪更改的内容和时间
* 如果更新了配置，则将破坏未直接链接到更新的内容的风险降至最低

>[!NOTE]
>
>有关设置工作流以自动导出包的详细信息，请参阅[此页](https://helpx.adobe.com/campaign/kb/export-packages-automatically.html)。

### 建议{#data-package-recommendations}

始终在平台的同一版本中导入。 您必须检查是否在两个具有相同内部版本的实例之间部署包。 切勿强制导入并始终先更新平台（如果内部版本不同）。

>[!IMPORTANT]
>
>Adobe不支持在不同版本之间导入。
<!--This is not allowed. Importing from 6.02 to 6.1, for example, is prohibited. If you do so, R&D won’t be able to help you resolve any issues you encounter.-->

注意模式和数据库结构。 必须先进口包装模式，然后再生成模式。

### 解决方案 {#data-package-solution}

#### 包类型{#package-types}

开始。 将仅使用四种类型：

**实体**
* Adobe Campaign中的所有“xtk”和“nms”特定元素，如模式、表单、文件夹、投放模板等。
* 您可以将实体视为“admin”和“platform”元素。
* 在包上传到活动实例时，不应在包中包含多个实体。

<!--Nothing “works” alone. An entity package does not have a specific role or objective.-->

如果需要在新实例上部署配置，可以导入所有实体包。

**功能**

此类包：
* 回答客户要求/规范。
* 包含一个或多个功能。
* 应包含所有依赖项，以便能够在没有任何其他包的情况下运行功能。

**营销策划**

此包不是必填的。 有时，为所有活动创建特定类型很有用，即使活动可以被视为功能。

**更新**

配置后，功能可导出到其他环境。 例如，可以将包从开发环境导出到测试环境。 在本实验中，发现了缺陷。 首先，它需要在开发环境上修复。 然后，应将补丁应用于测试平台。

第一个解决方案是再次导出整个功能。 但是，为了避免任何风险（更新不需要的元素），更安全的做法是只包含修正的包。

因此，我们建议创建一个“update”包，它只包含该功能的一个实体类型。

更新不仅可以是修复，而且可以是实体/功能/活动包的新元素。 要避免部署整个包，您可以导出更新包。

### 命名约定{#data-package-naming}

既然已定义类型，我们应指定命名约定。 Adobe Campaign不允许根据包规范创建子文件夹，这意味着数字是保持组织的最佳解决方案。 数字前缀包名。 您可以使用以下约定：

* 实体：从1到99
* 功能：从100到199
* 活动:从200到299
* 更新：从5000到5999

### 包{#data-packages}

>[!NOTE]
>
>最好设置规则来定义正确数量的包。

#### 实体包顺序{#entity-packages-order}

为了帮助导入，实体包应按导入时的顺序排列。 例如：
* 001 -模式
* 002 — 表单
* 003 — 图像
* 等。

>[!NOTE]
>
>Forms只应在更新模式后导入。

#### 包200 {#package-200}

包编号“200”不应用于特定活动:此数字将用于更新与所有活动相关的内容。

#### 更新包{#update-package}

最后一点涉及更新包编号。 它是包号(实体、功能或活动)，前缀为“5”。 例如：
* 5001更新一个模式
* 5200可更新所有活动
* 5101将更新101功能

更新包应仅包含一个特定实体，以便能够轻松地重用。 要拆分它们，请添加一个新数字(开始自1)。 这些包没有特定的订购规则。 为了更好地理解，请想象我们有一个101功能，一个社交应用：
* 它包含一个webApp和一个外部帐户。
   * 包标签为：101 — 社交应用(socialApplication)。
* webApp存在缺陷。
   * wepApp已更正。
   * 需要创建具有以下名称的修复包：5101 - 1 - Social应用程序webApp(socialApplication_webApp)。
* 需要为社交功能添加新的外部帐户。
   * 外部帐户已创建。
   * 新包是：5101 - 2 — 社交应用程序外部帐户(socialApplication_extAccount)。
   * 与此同时，101包将更新以添加到外部帐户，但不会部署它。
      ![](assets/ncs_datapackage_best-practices-1.png)

#### 包文档{#package-documentation}

更新包时，应始终在描述字段中添加注释以详细说明任何修改和原因(例如，“添加新模式”或“修复缺陷”)。

![](assets/ncs_datapackage_best-practices-2.png)

您还应将评论日期设置为。 始终将您对更新包的评论报告给“parent”（包中不含5前缀）。

>[!IMPORTANT]
>
>描述字段最多只能包含2.000个字符。
