---
product: campaign
title: 数据架构
description: Campaign数据架构入门
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Schema Extension
role: Data Engineer, Developer
exl-id: d4446035-3988-4d89-b7df-7b8528c2e371
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 3%

---

# 数据架构{#data-schemas}

## 原则 {#principles}

要编辑、创建和配置架构，请单击 **[!UICONTROL Administration > Configuration > Data schemas]** Adobe Campaign节点。

>[!NOTE]
>
>内置数据架构只能由Adobe Campaign Classic控制台的管理员删除。

![](assets/d_ncs_integration_schema_navtree.png)

编辑字段显示源架构的XML内容：

![](assets/d_ncs_integration_schema_edition.png)

>[!NOTE]
>
>通过“名称”编辑控件，可输入由名称和命名空间组成的架构键。 架构的根元素的“名称”和“命名空间”属性会在架构的XML编辑区域中自动更新。

预览会自动生成扩展架构：

![](assets/d_ncs_integration_schema_edition2.png)

>[!NOTE]
>
>保存源架构后，将自动启动扩展架构的生成。

如果需要检查架构的完整结构，可以使用预览选项卡。 如果架构已扩展，则随后您将能够可视化其所有扩展。 作为补充，“文档”选项卡显示所有方案属性和元素及其属性（SQL字段、类型/长度、标签、说明）。 “文档”选项卡仅适用于生成的架构。 有关详细信息，请参见 [重新生成模式](../../configuration/using/regenerating-schemas.md) 部分。

## 示例：创建合同表 {#example--creating-a-contract-table}

在以下示例中，我们要为 **合同** 在Adobe Campaign数据库的数据库模型中。 此表允许您存储每个合同的持有者和共同持有者的名字和姓氏以及电子邮件地址。

为此，您需要创建表的模式并更新数据库结构以生成相应的表。 应用以下阶段：

1. 编辑 **[!UICONTROL Administration > Configuration > Data schemas]** Adobe Campaign节点，然后单击 **[!UICONTROL New]** .
1. 选择 **[!UICONTROL Create a new table in the data model]** 选项并单击 **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_create_new_schema.png)

1. 指定表的名称和命名空间。

   ![](assets/s_ncs_configuration_create_new_param.png)

   >[!NOTE]
   >
   >默认情况下，用户创建的架构存储在“cus”命名空间中。 有关详细信息，请参见 [架构的标识](../../configuration/using/about-schema-reference.md#identification-of-a-schema).

1. 创建表的内容。 我们建议使用登录向导以确保没有缺少设置。 要执行此操作，请单击 **[!UICONTROL Insert]** 按钮，并选择要添加的设置的类型。

   ![](assets/s_ncs_configuration_create_new_content.png)

1. 定义合同表的设置：

   ```
   <srcSchema desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract" mappingType="sql" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <element desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract"
              name="Contracts" autopk="true">
              <attribute name="holderName" label="Holder last name" type="string"/>
              <attribute name="holderFirstName" label="Holder first name" type="string"/>
              <attribute name="holderEmail" label="Holder email" type="string"/>
              <attribute name="co-holderName" label="Co-holder last name" type="string"/>           
              <attribute name="co-holderFirstName" label="Co-holder first name" type="string"/>           
              <attribute name="co-holderEmail" label="Co-holder email" type="string"/>    
              <attribute name="date" label="Subscription date" type="date"/>     
              <attribute name="noContract" label="Contract number" type="long"/>  
     </element>
   </srcSchema>
   ```

   添加合同类型并对合同编号设置索引。

   ```
   <srcSchema _cs="Contracts (cus)" desc="Active contracts" entitySchema="xtk:srcSchema" img="ncm:channels.png"
              label="Contracts" labelSingular="Contract" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <enumeration basetype="byte" name="typeContract">
       <value label="Home" name="home" value="0"/>
       <value label="Car" name="car" value="1"/>
       <value label="Health" name="health" value="2"/>
       <value label="Pension fund" name="pension fund" value="2"/>
     </enumeration>
     <element autopk="true" desc="Active contracts" img="ncm:channels.png" label="Contracts"
              labelSingular="Contract" name="Contracts">
       <attribute label="Holder last name" name="holderName" type="string"/>
       <attribute label="Holder first name" name="holderFirstName" type="string"/>
       <attribute label="Holder email" name="holderEmail" type="string"/>
       <attribute label="Co-holder last name" name="co-holderName" type="string"/>
       <attribute label="Co-holder first name" name="co-holderFirstName" type="string"/>
       <attribute label="Co-holder email" name="co-holderEmail" type="string"/>
       <attribute label="Subscription date" name="date" type="date"/>
      <attribute desc="Type of contract" enum="cus:Contracts:typeContract" label="Type of contract"
                  name="type" type="byte"/>
       <attribute label="Contract number" name="noContract" type="long"/>
       <dbindex name="noContract" unique="true">
         <keyfield xpath="@noContract"/>
       </dbindex>
     </element>
   </srcSchema>
   ```

1. 保存架构以生成结构：

   ![](assets/s_ncs_configuration_structure.png)

1. 更新数据库结构以创建将链接架构的表。 有关详细信息，请参见 [更新数据库结构](../../configuration/using/updating-the-database-structure.md).
