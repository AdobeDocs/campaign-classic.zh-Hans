---
title: 种子地址
seo-title: 种子地址
description: 种子地址
seo-description: null
page-status-flag: never-activated
uuid: 0ebdeb73-be67-4c34-9f59-9fd4fb5241ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 41338d32-b95c-45ae-bee6-17b2af5bd837
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d5c1732858fd5d079bbd9a755997c04adf5c9d47

---


# 种子地址{#seed-addresses}

如果收件人表是自定义表，则需要其他配置。 必 **[!UICONTROL nms:seedMember]** 须延长模式。 种子地址中会添加一个用于定义适当字段的附加选项卡，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

有关使用种子地址的详细信息，请参 [阅本节](../../delivery/using/about-seed-addresses.md)。

## 实施 {#implementation}

**nms:seedMember** 模式和现成的链接表单旨在扩展用于客户配置，以引用所有必要字段。 模式定义包含详细描述其配置模式的注释。

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

1. 创建 **nms:seedMember模式的扩展** 。 有关此问题的详细信息，请参 [阅扩展模式](../../configuration/using/extending-a-schema.md)。
1. 在此新扩展中，在的根添加一个新元素， **[!UICONTROL seedMember]** 并使用以下参数：

   ```
   name="custom_customNamespace_customSchema"
   ```

   此元素必须包含导出活动所需的字段。 这些字段应与外部模式中的相应字段同名。 例如，如果模式为 **[!UICONTROL cus:person]** , **[!UICONTROL nms:seedMember]** 则模式应按如下方式扩展：

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
   >nms:seedMember模式的扩 **** 展必须符合活动和Adobe Campaign中投放的结构。

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * 在扩展过程中，必须为“ **email”字段指定SQL名称(@sqlname)** 。 SQL名称必须与为收件人模式保留的&#39;sEmail&#39;不同。
   >    * 必须使用在扩展 **nms:seedMember时创建的模式更新数据库结构**。
   >    * 在 **nms:seedMember** extension中，包含电子邮件地址的字段必须 **将name=&quot;email&quot;** 作为属性。 SQL名称必须不同于已用于收件人模式的“sEmail”。 此属性必须立即在元素下声明 **`<element name="custom_cus_person" />`** 。


1. 相应地修 **[!UICONTROL seedMember]** 改表单，以在窗口中定义新的“内部收件人”选 **[!UICONTROL Seed addresses]** 项卡。 For more on this, refer to [Form structure](../../configuration/using/form-structure.md).

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

如果未输入种子地址的所有属性，则Adobe Campaign会自动替换用户档案:在个性化过程中，将使用现有用户档案中的数据自动输入这些内容。
