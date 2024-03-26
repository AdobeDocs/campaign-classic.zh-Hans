---
product: campaign
title: 种子地址
description: 种子地址
role: Data Engineer, Developer
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Seed Address
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 8%

---

# 种子地址{#seed-addresses}



如果收件人表是自定义表，则需要其他配置。 此 **[!UICONTROL nms:seedMember]** 必须扩展架构。 向种子地址添加了一个附加选项卡，用于定义适当的字段，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

有关使用种子地址的详细信息，请参阅 [本节](../../delivery/using/about-seed-addresses.md).

## 实现 {#implementation}

此 **nms：seedMember** 现成的架构和链接表单经过扩展可用于客户配置，以引用所有必需的字段。 架构定义包含详细说明其配置模式的注释。

收件人表扩展模式的定义：

```
<srcSchema label="Person" name="person" namespace="cus">
  <element autopk="true" label="Person" name="person">
      <attribute label="LastName" name="lastname" type="string"/>
      <attribute label="FirstName" name="firstname" type="string"/>
    <element label="Address" name="address">
      <attribute label="Email" name="addrEnv" type="string"/>
    </element>
    <attribute label="Code Offer" name="codeOffer" type="string"/>
  </element>
</srcSchema>
```

应用以下步骤：

1. 创建 **nms：seedMember** 架构。 如需详细信息，请参阅[此小节](../../configuration/using/extending-a-schema.md)。
1. 在此新扩展中，在的根目录下添加新元素 **[!UICONTROL seedMember]** ，并使用以下参数：

   ```
   name="custom_customNamespace_customSchema"
   ```

   此元素必须包含导出营销活动所需的字段。 这些字段应与外部架构中对应的字段具有相同的名称。 例如，如果架构为 **[!UICONTROL cus:person]** ， **[!UICONTROL nms:seedMember]** 架构应按如下方式进行扩展：

   ```
     <srcSchema extendedSchema="nms:seedMember" label="Seed addresses" labelSingular="Seed address" name="seedMember" namespace="cus">
     <element name="common">
       <element name="custom_cus_person">
         <attribute name="lastname" template="cus:person:person/@lastname"/>
         <attribute name="firstname" template="cus:person:person/@firstname"/>
         <attribute name="email" sqlname="myEmailField" template="cus:person:person/address/@addrEnv" xml="false"/>
       </element>
     </element>
     <element name="seedMember">
      <element aggregate="cus:seedMember:common"/>
     </element>
   </srcSchema>
   ```

   >[!NOTE]
   >
   >的扩展 **nms：seedMember** 架构必须符合Adobe Campaign中营销活动和投放的结构。

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * 在扩展过程中，您必须指定 **SQL名称(@sqlname)** （对于“email”字段）。 SQL名称必须与为收件人架构保留的“sEmail”不同。
   >    * 必须使用扩展时创建的模式更新数据库结构 **nms：seedMember**.
   >    * 在 **nms：seedMember** 扩展名，包含电子邮件地址的字段必须具有 **name=&quot;email&quot;** 作为属性。 SQL名称必须与已用于收件人架构的“sEmail”不同。 此属性必须立即声明在 **`<element name="custom_cus_person" />`** 元素。
   >    
   >

1. 修改 **[!UICONTROL seedMember]** 表单，以在中定义新的“内部收件人”选项卡 **[!UICONTROL Seed addresses]** 窗口。 有关详细信息，请参见[此页面](../../configuration/using/form-structure.md)。

   ```
   <container colcount="2" label="Internal recipient" name="internal"
                xpath="custom_cus_person">
       <input colspan="2" editable="true" nolabel="true" type="treeEdit">
         <container label="Recipient (cus:person)">
           <input xpath="@last name"/>
           <input xpath="@first name"/>
           <input xpath="@email"/>
         </container>
       </input>
     </container>
   ```

如果未输入种子地址的所有属性，则Adobe Campaign会自动替换用户档案：在个性化过程中，将使用现有用户档案中的数据自动输入这些属性。
