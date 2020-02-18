---
title: 配置界面
seo-title: 配置界面
description: 配置界面
seo-description: null
page-status-flag: never-activated
uuid: 101ba02f-da43-4dcc-b9ff-6e5ca848fc5d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 8fb9ff23-17a7-4425-9195-738d6fd914dc
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 配置界面{#configuring-the-interface}

要在Adobe Campaign界面中查看新收件人表并与其对话，请应用以下步骤：

* 创建新表单以编辑新收件人表的内容。
* 在资源管理器树的文件夹中输入新类型。
* 创建新的Web应用程序，通过Adobe Campaign主页访问自定义表。

Adobe Campaign使用“Nms_DefaultRcpSchema”全局变量与默认收件人数据库(nms:recipient)进行对话。 因此，需要更改此变量。

1. 转到资 **[!UICONTROL Administration>Platform>Options]** 源管理器的节点。
1. 使用与外部收件人表匹配的 **架构名称更改Nms_DefaultRcpSchema** 变量的值(在本例中为：cus:individual)。
1. 保存更改。

## 创建新表单 {#creating-a-new-form-}

创建新表单后，您可以查看和编辑外部收件人表格的数据。

>[!IMPORTANT]
>
>表单的名称必须与其所关注的架构的名称相同。

1. 转到资源管理器 **的“管理”>“配置”** >“输入表单”节点。
1. 创建新 **xtk:form** **type form** 文件。
1. 根据表模板描述您需要的所有监视器和字段。

   >[!NOTE]
   >
   >要进一步了解表 **单类型** ，请参阅 [本页](../../configuration/using/identifying-a-form.md)。

   在我们的当前示例中， **表单文件必须** 基于cus:individual **** schema，因此具有以下布局：

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

1. 转到节 **[!UICONTROL Administration>Configuration>Navigation hierarchies]** 点。
1. 创建新 **xtk:navtree** type **navtree文档** 。
1. 根据表模板描述您需要的所有监视器和字段。

   >[!NOTE]
   >
   >有关navtree类 **型文件的详** 细信息，请参 [阅此页](../../configuration/using/about-navigation-hierarchy.md)。

   在当前示例中， **navtree** 文件必须基于 **** cus:individual架构，因此具有以下表单：

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

