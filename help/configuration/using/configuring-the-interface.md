---
solution: Campaign Classic
product: campaign
title: 配置接口
description: 配置接口
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
translation-type: tm+mt
source-git-commit: d7eabfbebf016d2632d95d34a5b36719ccc1d88a
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---

# 配置接口{#configuring-the-interface}

要视图并与Adobe Campaign界面中新的收件人表对话，请应用以下步骤：

* 创建新表单以编辑新收件人表的内容。
* 在资源管理器树的文件夹中输入新类型。
* 创建一个新的Web应用程序以通过Adobe Campaign主页访问自定义表。

Adobe Campaign使用“Nms_DefaultRcpSchema”全局变量与默认收件人数据库(nms:收件人)对话。 因此，需要更改此变量。

1. 转到资源管理器的&#x200B;**[!UICONTROL Administration>Platform>Options]**&#x200B;节点。
1. 使用与外部收件人表匹配的模式名称更改&#x200B;**Nms_DefaultRcpSchema**&#x200B;变量的值(在本例中为：cus:individual)。
1. 保存更改。

## 创建新表单{#creating-a-new-form-}

创建新表单后，您可以视图和编辑外部收件人表的数据。

>[!IMPORTANT]
>
>表单的名称必须与其所关注的模式的名称相同。

1. 转到资源管理器的&#x200B;**管理>配置>输入表单**&#x200B;节点。
1. 新建一个&#x200B;**xtk:form**&#x200B;类型&#x200B;**form**&#x200B;文件。
1. 根据表模板描述所需的所有监视器和字段。

   >[!NOTE]
   >
   >要查找有关&#x200B;**form**&#x200B;类型文件的详细信息，请参阅[此页](../../configuration/using/identifying-a-form.md)。

   在我们的当前示例中，**form**&#x200B;文件必须基于&#x200B;**cus:individual**&#x200B;模式，因此具有以下布局：

   ```
   <container colspan="2">
       <input xpath="@id"/>
       <static type="separator"/>
   </container>
   <container colcount="2">
       <input xpath="@lastName"/>
       <input xpath="@firstName"/>
       <input xpath="@email"/>
       <input xpath="@mobile"/>
   </container> 
   ```

1. 保存创建。

## 在导航层次结构{#creating-a-new-type-of-folder-in-the-navigation-hierarchy}中创建新类型的文件夹

1. 转到&#x200B;**[!UICONTROL Administration>Configuration>Navigation hierarchies]**&#x200B;节点。
1. 新建一个&#x200B;**xtk:navtree**&#x200B;类型&#x200B;**navtree**&#x200B;文档。
1. 根据表模板描述所需的所有监视器和字段。

   >[!NOTE]
   >
   >有关&#x200B;**navtree**&#x200B;类型文件的详细信息，请参阅[此页面](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy)。

   在当前示例中，**navtree**&#x200B;文件必须基于&#x200B;**cus:individual**&#x200B;模式，因此具有以下格式：

   ```
    <model name="root">
       <nodeModel img="nms:usergrp.png" label="My recipient table" name="cusindividual">
         <view name="listdet" schema="cus:individual" type="listdet">
           <columns>
             <node xpath="@id"/>
             <node xpath="@lastName"/>
             <node xpath="@firstName"/>
             <node xpath="@email"/>
             <node xpath="@mobile"/>
           </columns>
         </view>
       </nodeModel>
   </model>
   ```

1. 保存创建。
