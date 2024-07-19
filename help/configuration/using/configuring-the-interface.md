---
product: campaign
title: 配置接口
description: 了解如何配置Campaign界面
feature: Application Settings
role: Data Engineer, Developer
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# 配置接口{#configuring-the-interface}

要在Adobe Campaign界面中查看新收件人表并与其对话，请应用以下步骤：

* 创建新表单以编辑新收件人表的内容。
* 在浏览器树的文件夹中输入新类型。
* 创建新的Web应用程序，以通过Adobe Campaign主页访问自定义表。

Adobe Campaign使用“Nms_DefaultRcpSchema”全局变量与默认收件人数据库(nms：recipient)进行对话。 因此，需要更改此变量。

1. 转到资源管理器的&#x200B;**[!UICONTROL Administration>Platform>Options]**&#x200B;节点。
1. 将&#x200B;**Nms_DefaultRcpSchema**&#x200B;变量的值更改为与外部收件人表匹配的架构名称（在本例中为cus：individual）。
1. 保存更改。

## 创建新表单 {#creating-a-new-form-}

创建新表单后，您可以查看和编辑外部收件人表的数据。

>[!IMPORTANT]
>
>表单的名称必须与它涉及的架构的名称相同。

1. 转到资源管理器的&#x200B;**管理>配置>输入表单**&#x200B;节点。
1. 创建新的&#x200B;**xtk：form**&#x200B;类型&#x200B;**表单**&#x200B;文件。
1. 根据表模板说明所需的所有监视和字段。

   >[!NOTE]
   >
   >要了解有关&#x200B;**表单**&#x200B;类型文件的详细信息，请参阅[此页面](../../configuration/using/identifying-a-form.md)。

   在我们的当前示例中，**form**&#x200B;文件必须基于&#x200B;**cus：individual**&#x200B;架构，因此具有以下布局：

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

## 在导航层次结构中创建新类型的文件夹 {#creating-a-new-type-of-folder-in-the-navigation-hierarchy}

1. 转到&#x200B;**[!UICONTROL Administration>Configuration>Navigation hierarchies]**&#x200B;节点。
1. 创建新的&#x200B;**xtk：navtree**&#x200B;类型&#x200B;**navtree**&#x200B;文档。
1. 根据表模板说明所需的所有监视和字段。

   >[!NOTE]
   >
   >有关&#x200B;**导航树**&#x200B;类型文件的详细信息，请参阅[此页面](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy)。

   在当前示例中，**navtree**&#x200B;文件必须基于&#x200B;**cus：individual**&#x200B;架构，因此具有以下形式：

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
