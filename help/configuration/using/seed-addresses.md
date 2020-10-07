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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 3%

---


# 种子地址{#seed-addresses}

如果收件人表是自定义表，则需要其他配置。 必 **[!UICONTROL nms:seedMember]** 须延长模式。 在种子地址中会添加一个额外的选项卡，用于定义适当的字段，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

有关使用种子地址的详细信 [息，请参阅](../../delivery/using/about-seed-addresses.md)。

## 实施 {#implementation}

nms **:seedMember** 模式和现成附带的链接表单旨在扩展用于客户配置，以引用所有必要字段。 模式定义包含详细描述其配置模式的注释。

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

1. 创建nms:seedMember **模式的扩展** 。 有关此内容的详细信息，请参 [阅扩展模式](../../configuration/using/extending-a-schema.md)。
1. 在此新扩展中，使用以下参数在的根 **[!UICONTROL seedMember]** 添加新元素：

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
   >nms:seedMember模式 **的扩展** ，必须符合Adobe Campaign中活动和投放的结构。

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * 在扩展期间，必须为“ **email”字段指定SQL名称** (@sqlname)。 SQL名称必须与为收件人模式保留的&#39;sEmail&#39;不同。
   >    * 必须使用在扩展nms:seedMember时创建的模式更 **新库结构**。
   >    * 在nms: **seedMember** extension中，包含电子邮件地址的字段 **必须将name=&quot;email** &quot;作为属性。 SQL名称必须与已用于收件人模式的&#39;sEmail&#39;不同。 此属性必须立即在元素下声 **`<element name="custom_cus_person" />`** 明。


1. 相应地 **[!UICONTROL seedMember]** 修改表单以在窗口中定义新的“内部收件人” **[!UICONTROL Seed addresses]** 选项卡。 For more on this, refer to [Form structure](../../configuration/using/form-structure.md).

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

如果未输入种子地址的所有属性，Adobe Campaign会自动替换用户档案:它们将在个性化过程中使用来自现有用户档案的数据自动输入。
