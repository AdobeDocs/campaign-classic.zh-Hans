---
solution: Campaign Classic
product: campaign
title: 配置接口
description: 配置接口
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---


# 配置接口{#configuring-the-interface}

要视图并与Adobe Campaign界面中的新收件人表对话，请应用以下步骤：

* 创建新表单以编辑新收件人表的内容。
* 在资源管理器树的文件夹中输入新类型。
* 创建新的Web应用程序，通过Adobe Campaign主页访问自定义表。

Adobe Campaign使用“Nms_DefaultRcpSchema”全局变量与默认收件人数据库(nms:收件人)对话。 因此，需要更改此变量。

1. 转到资 **[!UICONTROL Administration>Platform>Options]** 源管理器的节点。
1. 使用与外部模式 **表匹配的收件人名** ，更改Nms_DefaultRcpSchema变量的值(在本例中：cus:individual)。
1. 保存更改。

## Creating a new form {#creating-a-new-form-}

创建新表单后，您可以视图和编辑外部收件人表的数据。

>[!IMPORTANT]
>
>表单的名称必须与其所关注的模式的名称相同。

1. 转到资源管理器 **的“管理”>“配置”** >“输入表单”节点。
1. 新建一个 **xtk:form** type **form** file。
1. 根据表模板描述您需要的所有监视器和字段。

   >[!NOTE]
   >
   >要进一步了解表 **单类** 型文件，请 [参阅此页](../../configuration/using/identifying-a-form.md)。

   在我们的当前示例 **中** ，表单文件必 **须基于cus:individual** 模式，因此具有以下布局：

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

1. Go to the **[!UICONTROL Administration>Configuration>Navigation hierarchies]** node.
1. 新建一 **个xtk:navtree** type **navtree** 文档。
1. 根据表模板描述您需要的所有监视器和字段。

   >[!NOTE]
   >
   >有关navtree类 **型文** 件的详细信息， [请参阅此页](../../configuration/using/about-navigation-hierarchy.md)。

   在当前示例中， **navtree** 文件必须基于 **cus:individual** 模式，因此具有以下格式：

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

