---
title: 使用数据包
seo-title: 使用数据包
description: 使用数据包
seo-description: null
page-status-flag: never-activated
uuid: 867b2702-dbc4-4b71-a385-a2c7fd09d25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: 42867665-d0ca-486e-9110-91716c0d5c57
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 使用数据包{#working-with-data-packages}

## 关于数据包 {#about-data-packages}

使用 Adobe Campaign，您可以通过数据包系统导出或导入平台配置和数据。包可以包含不同类型的配置、元素、已过滤或不已过滤。

数据包支持以 XML 格式文件的形式显示 Adobe Campaign 数据库的实体。数据包中包含的每个实体由其全部数据表示。

The principle of **data packages** is to export a data configuration and integrate it into another Adobe Campaign system. 有关如何维护一组一致的数据包的详细信息，请参阅此技 [术说明](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_How_to_maintain_a_consistent_set_of_data_packages.pdf)。

### 包类型 {#types-of-packages}

可导出包有三种类型：用户包、平台包和管理员包。

* **用户包**:它允许您选择要导出的图元列表。 此类包管理依赖关系并验证错误。
* **平台包**:它包含所有附加的技术资源（非标准）:架构、JavaScript代码等。

   ![](assets/ncs_datapackage_package_platform.png)

* **管理包**:它包括所有添加的模板和业务对象（非标准）:模板、库等。

   ![](assets/ncs_datapackage_package_admin.png)

>[!CAUTION]
>
>平 **台和管** 理员类 **** 型包含要导出的实体的预定义列表。 每个实体都链接到过滤条件，这些条件允许您删除创建的包的现成资源。

## 数据结构 {#data-structure}

数据包的描述是符合 **xrk:navtree数据架构的语法的结构化XML文档** 。

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

XML文档必须以元素开头和结 **`<package>`** 尾。 随后 **`<entities>`** 的任何元素都会按文档类型分发数据。

元 **`<entities>`** 素包含在schema属性中输入的数据架构格式的包 **数据** 。

包中的数据不能包含基本之间不兼容的内部密钥，如自动生成的密钥(自动&#x200B;**选项** )。

在我们的示例中，“文件夹”和“公司”链接上的连接已被目标表上的所谓“高级”键所取代：

```
<recipient>
  <folder _operation="none" name="nmsRootFolder"/>
  <company _operation="none" name="Adobe"/>
</recipient>
```

值 **`operation`** 为“none”的属性定义协调链接。

可以从任何文本编辑器手动构建数据包。 只需确保XML文档的结构符合“xtk:navtree”数据架构。 Adobe Campaign控制台有一个数据包导出和导入模块。

## 导出包 {#exporting-packages}

### 关于包导出 {#about-package-export}

可以通过三种不同的方式导出包：

* 使 **[!UICONTROL Package Export Wizard]** 用它可以导出单个包中的一组对象。 有关详细信息，请参 [阅导出包中的一组对象](#exporting-a-set-of-objects-in-a-package)
* 可 **以通过右键单击** “对象”并选择，在包中直接导出单个对象 **[!UICONTROL Actions > Export in a package]**。
* **包定义** ，允许您创建包结构，在其中添加对象，这些对象稍后将在包中导出。 有关此功能的详细信息，请参阅管 [理包定义](#managing-package-definitions)

导出包后，您将能够将它和所有添加的实体导入另一个营销活动实例。

### 导出包中的一组对象 {#exporting-a-set-of-objects-in-a-package}

包导出向导可通过Adobe Campaign客 **[!UICONTROL Tools > Advanced > Export package...]** 户端控制台的菜单访问。

![](assets/ncs_datapackage_typepackage.png)

对于这三种类型的包，向导提供以下步骤：

1. 按文档类型列出要导出的实体：

   ![](assets/ncs_datapackage_export2.png)

   >[!CAUTION]
   >
   >如果导出文 **[!UICONTROL Offer category]**&#x200B;件夹、 **[!UICONTROL Offer environment]****[!UICONTROL Program]** 或类型文 **[!UICONTROL Plan]** 件夹，则不要选择xtk:folder **** ，因为您可能会丢失一些数据。 选择与文件夹对应的实体： **nms:offerCategory** for offer **,** nms:offerEnv **for offer environments,** nms:program **for program, and** nms:plan for plans.

   列表管理允许您添加或删除要从配置中导出的实体。 单击 **[!UICONTROL Add]** 以选择新实体。

   该按 **[!UICONTROL Detail]** 钮可编辑选定的配置。

   >[!NOTE]
   >
   >依赖关系机制控制实体导出序列。 For more on this, refer to [Managing dependencies](#managing-dependencies).

1. 实体配置屏幕定义对要提取的文档类型的过滤器查询。

   必须为数据提取配置过滤子句。

   ![](assets/ncs_datapackage_export4.png)

   >[!NOTE]
   >
   >此部分显示查询编 [辑器](../../platform/using/about-queries-in-campaign.md)。

1. 单击 **[!UICONTROL Next]** 并选择排序列，以在提取过程中对数据进行排序：

   ![](assets/ncs_datapackage_export5.png)

1. 运行导出之前，预览要提取的数据。

   ![](assets/ncs_datapackage_export6.png)

1. 在包导出向导的最后一页中，可以启动导出。 数据将存储在字段中指示的文件 **[!UICONTROL File]** 中。

   ![](assets/ncs_datapackage_export7.png)

### 管理依赖关系 {#managing-dependencies}

导出机制使Adobe Campaign能够跟踪各种导出元素之间的链接。

此机制由两个规则定义：

* 链接到链接的对象具有 **自己的****或下的复制类型完整性** ，这些对象将导出到与导出对象相同的包中。
* 链接到具有中性链接的对象 **或定义类型****完整性(定义的链接** )的对象必须单独导出。

>[!NOTE]
>
>本节中定义了链接到架构元素的完整 [性类型](../../configuration/using/database-mapping.md#links--relation-between-tables)。

#### 导出营销活动 {#exporting-a-campaign}

以下是如何导出营销活动的示例。 要导出的营销活动包含一个任务(标签：“MyTask”)和工作流(标签：“MyWorkflow”文件夹(节点：管理／生产／技术工作流／营销活动流程/ myWorkflow)。

任务和工作流将导出到与营销活动相同的包中，因为匹配的架构通过具有“自己”类型完整性的链接连接。

打包内容：

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

在具有@pkgAdmin和@pkgPlatform属性的架构中定义了与某 **类包的从属关系** 。 这两个属性都接收一个XTK表达式，它定义与包的从属关系条件。

```
<element name="offerEnv" img="nms:offerEnv.png" 
template="xtk:folder" pkgAdmin="@id != 0">
```

最后， **@pkgStatus** 属性允许您为这些元素或属性定义导出规则。 根据属性的值，元素或属性将在导出的包中找到。 此属性的三个可能值是：

* **never**:不导出字段／链接
* **always**:这个领域的出口
* **preCreate**:授权创建链接的实体

>[!NOTE]
>
>仅链 **接类型事件** 才允许preCreate值。 它授权您创建或指向尚未加载到导出包中的实体。

## 管理包定义 {#managing-package-definitions}

### 关于包定义 {#about-package-definitions}

包定义允许您创建包结构，在其中添加稍后将在单个包中导出的实体。 然后，您将能够将此包和所有添加的实体导入到另一个营销活动实例中。

**相关主题：**

* [创建包定义](#creating-a-package-definition)
* [将实体添加到包定义](#adding-entities-to-a-package-definition)
* [配置包定义生成](#configuring-package-definitions-generation)
* [从包定义导出包](#exporting-packages-from-a-package-definition)

### 创建包定义 {#creating-a-package-definition}

可从菜单访问包定 **[!UICONTROL Administration > Configuration > Package management > Package definitions]** 义。

要创建包定义，请单击按 **[!UICONTROL New]** 钮，然后填写包定义一般信息。

![](assets/packagedefinition_create.png)

然后，可以向包定义中添加实体，并将其导出到XML文件包。

**相关主题：**

* [将实体添加到包定义](#adding-entities-to-a-package-definition)
* [配置包定义生成](#configuring-package-definitions-generation)
* [从包定义导出包](#exporting-packages-from-a-package-definition)

### 将实体添加到包定义 {#adding-entities-to-a-package-definition}

在选项 **[!UICONTROL Content]** 卡中，单击按 **[!UICONTROL Add]** 钮以选择要与包一起导出的实体。 在导出包中的一组对象部分中 [介绍了选择实体的最佳实践](#exporting-a-set-of-objects-in-a-package) 。

![](assets/packagedefinition_addentities.png)

实体可以直接从它们在实例中的位置添加到包定义。 为此请执行以下操作步骤：

1. 右键单击所需的实体，然后选择 **[!UICONTROL Actions > Export in a package]**。

   ![](assets/packagedefinition_singleentity.png)

1. 选 **[!UICONTROL Add to a package definition]**&#x200B;择，然后选择要添加实体的包定义。

   ![](assets/packagedefinition_packageselection.png)

1. 实体将添加到包定义中，它将随包一起导出(请参阅从包 [定义导出包](#exporting-packages-from-a-package-definition))。

   ![](assets/packagedefinition_entityadded.png)

### 配置包定义生成 {#configuring-package-definitions-generation}

可以从包定义选项卡中配置包生 **[!UICONTROL Content]** 成。 要执行此操作，请单击链 **[!UICONTROL Generation parameters]** 接。

![](assets/packagedefinition_generationparameters.png)

* **[!UICONTROL Include the definition]**:包括包定义中当前使用的定义。
* **[!UICONTROL Include an installation script]**:允许您添加要在包导入时执行的javascript脚本。 选中后，将在 **[!UICONTROL Script]** 包定义屏幕中添加一个选项卡。
* **[!UICONTROL Include default values]**:向包中添加所有实体属性的值。

   为避免冗长的导出，默认情况下不选择此选项。 这意味着具有默认值（“空字符串”、“0”和“false”，如果未在架构中另行定义）的实体属性不会添加到包中，因此不会导出。

   >[!CAUTION]
   >
   >取消选择此选项可能会导致合并本地版本和导入的版本。
   >
   >如果导入包的实例包含与包的实体相同的实体（例如，具有相同的外部ID），则不会更新其属性。 如果前一个实例的属性具有默认值（因为这些属性不包含在包中），则会发生这种情况。
   >
   >在这种情况下，选择该选 **[!UICONTROL Include default values]** 项将阻止版本合并，因为前实例的所有属性都将与包一起导出。

### 从包定义导出包 {#exporting-packages-from-a-package-definition}

要从包定义中导出包，请执行以下步骤：

1. 选择要导出的包定义，然后单击按 **[!UICONTROL Actions]** 钮并选择 **[!UICONTROL Export the package]**。
1. 默认情况下，与导出的包对应的XML文件处于选中状态。 它根据包定义命名空间和名称命名。
1. 定义包名称和位置后，单击 **[!UICONTROL Start]** 按钮以启动导出。

   ![](assets/packagedefinition_packageexport.png)

## 导入包 {#importing-packages}

### 关于包导入 {#about-package-import}

包导入向导可通过Adobe Campaign客户端控制台 **[!UICONTROL Tools > Advanced > Package import...]** 的主菜单访问。

您可以从先前执行的导出导入包，例如从其他Adobe Campaign实例或标准包导入包，具体取决于许可条款。

![](assets/ncs_datapackage_import.png)

### 从文件安装包 {#installing-a-package-from-a-file}

要导入现有数据包，请选择XML文件，然后单击 **[!UICONTROL Open]**。

![](assets/ncs_datapackage_import_1.png)

然后，要导入的包的内容将显示在编辑器的中间部分。

单击 **[!UICONTROL Next]** 并 **[!UICONTROL Start]** 启动导入。

![](assets/ncs_datapackage_import_2.png)

### 安装标准包 {#installing-a-standard-package}

配置Adobe Campaign时，将安装标准包。 根据您的权限和部署模型，如果您获得了新选项或加载项，或者升级到新选件，则可以导入新的标准包。

请参阅您的许可协议以检查可以安装的包。

有关标准包的详细信息，请参阅 [本页](../../installation/using/installing-campaign-standard-packages.md)。
