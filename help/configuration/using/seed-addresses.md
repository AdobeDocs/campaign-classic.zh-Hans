---
product: campaign
title: 种子地址
description: 种子地址
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Seed Address
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 8%

---

# 种子地址{#seed-addresses}



如果收件人表是自定义表，则需要额外的配置。 的 **[!UICONTROL nms:seedMember]** 必须扩展架构。 种子地址中添加了一个用于定义适当字段的附加选项卡，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

有关使用种子地址的更多信息，请参阅 [此部分](../../delivery/using/about-seed-addresses.md).

## 实施 {#implementation}

的 **nms:seedMember** 架构和现成链接表单用于扩展以用于客户配置，以引用所有必需字段。 架构定义包含详细描述其配置模式的注释。

收件人表扩展架构的定义：

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

1. 创建的扩展 **nms:seedMember** 架构。 如需详细信息，请参阅[此部分](../../configuration/using/extending-a-schema.md)。
1. 在此新扩展中，在的根下添加新元素 **[!UICONTROL seedMember]** 使用以下参数：

   ```
   name="custom_customNamespace_customSchema"
   ```

   此元素必须包含导出促销活动所需的字段。 这些字段应与外部架构中的相应字段同名。 例如，如果架构为 **[!UICONTROL cus:person]** , **[!UICONTROL nms:seedMember]** 架构的扩展应如下所示：

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
   >的扩展 **nms:seedMember** 架构必须符合Adobe Campaign中营销活动和投放的结构。

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * 在扩展期间，您必须指定 **SQL名称(@sqlname)** “email”字段。 SQL名称必须不同于为收件人架构保留的sEmail名称。
   >    * 必须使用扩展时创建的模式更新数据库结构 **nms:seedMember**.
   >    * 在 **nms:seedMember** 扩展中，包含电子邮件地址的字段必须具有 **name=&quot;email&quot;** 属性。 SQL名称必须不同于已用于收件人架构的“sEmail”。 此属性必须立即在 **`<element name="custom_cus_person" />`** 元素。


1. 修改 **[!UICONTROL seedMember]** 表单，以在 **[!UICONTROL Seed addresses]** 窗口。 有关详细信息，请参见[此页面](../../configuration/using/form-structure.md)。

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

如果未输入种子地址的所有属性，则Adobe Campaign会自动替换用户档案：在个性化期间，将使用现有用户档案的数据自动输入这些用户档案。
