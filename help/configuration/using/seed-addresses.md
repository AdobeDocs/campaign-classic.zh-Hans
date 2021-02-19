---
solution: Campaign Classic
product: campaign
title: 种子地址
description: 种子地址
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 3%

---


# 种子地址{#seed-addresses}

如果收件人表是自定义表，则需要其他配置。 **[!UICONTROL nms:seedMember]**&#x200B;模式必须扩展。 “种子地址”中会添加一个附加选项卡，用于定义适当的字段，如下所示：

![](assets/s_ncs_user_seedlist_new_tab.png)

有关使用种子地址的详细信息，请参阅[本节](../../delivery/using/about-seed-addresses.md)。

## 实现{#implementation}

**nms:seedMember**&#x200B;模式和附带的现成链接表单旨在扩展用于客户配置，以引用所有必要字段。 模式定义包含详细描述其配置模式的注释。

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

1. 创建&#x200B;**nms:seedMember**&#x200B;模式的扩展。 有关详细信息，请参阅[扩展模式](../../configuration/using/extending-a-schema.md)。
1. 在此新扩展中，使用以下参数在&#x200B;**[!UICONTROL seedMember]**&#x200B;的根添加一个新元素：

   ```
   name="custom_customNamespace_customSchema"
   ```

   此元素必须包含导出活动所需的字段。 这些字段应与外部模式中的相应字段同名。 例如，如果模式为&#x200B;**[!UICONTROL cus:person]**，则&#x200B;**[!UICONTROL nms:seedMember]**&#x200B;模式应按如下方式扩展：

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
   >**nms:seedMember**&#x200B;模式的扩展必须符合Adobe Campaign中活动和投放的结构。

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * 在扩展期间，必须为“email”字段指定&#x200B;**SQL名称(@sqlname)**。 SQL名称必须与为收件人模式保留的&#39;sEmail&#39;不同。
   >    * 必须使用在扩展&#x200B;**nms:seedMember**&#x200B;时创建的模式更新数据库结构。
   >    * 在&#x200B;**nms:seedMember**&#x200B;扩展中，包含电子邮件地址的字段必须具有&#x200B;**name=&quot;email&quot;**&#x200B;作为属性。 SQL名称必须不同于已用于收件人模式的&#39;sEmail&#39;。 此属性必须立即在&#x200B;**`<element name="custom_cus_person" />`**&#x200B;元素下声明。


1. 相应地修改&#x200B;**[!UICONTROL seedMember]**&#x200B;表单，以在&#x200B;**[!UICONTROL Seed addresses]**&#x200B;窗口中定义新的“内部收件人”选项卡。 有关详细信息，请参阅[表单结构](../../configuration/using/form-structure.md)。

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

如果未输入种子地址的所有属性，Adobe Campaign会自动替换用户档案:它们将在个性化过程中使用现有用户档案中的数据自动输入。
