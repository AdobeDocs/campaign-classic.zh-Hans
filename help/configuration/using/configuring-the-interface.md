---
product: campaign
title: 配置接口
description: 配置接口
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 9f50f258-845e-4895-b1ef-b73744dea326
source-git-commit: fb4b4c42b907e86813ea570f912312fccf893bfe
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 2%

---

# 配置接口{#configuring-the-interface}

![](../../assets/common.svg)

要在Adobe Campaign界面中查看新收件人表并与之对话，请应用以下步骤：

* 创建新表单以编辑新收件人表的内容。
* 在资源管理器树的文件夹中输入新类型。
* 创建新的Web应用程序以通过Adobe Campaign主页访问自定义表。

Adobe Campaign使用“Nms_DefaultRcpSchema”全局变量与默认收件人数据库(nms:recipient)对话。 因此，需要更改此变量。

1. 转到 **[!UICONTROL Administration>Platform>Options]** 资源管理器的节点。
1. 更改 **Nms_DefaultRcpSchema** 变量，其名称与外部收件人表匹配的架构(在本例中为：cus:indival)。
1. 保存更改。

## 创建新表单 {#creating-a-new-form-}

创建新表单后，您可以查看和编辑外部收件人表的数据。

>[!IMPORTANT]
>
>表单的名称必须与其所关注架构的名称相同。

1. 转到 **管理>配置>输入表单** 资源管理器的节点。
1. 新建 **xtk:form** type **表单** 文件。
1. 根据表模板描述您需要的所有监视和字段。

   >[!NOTE]
   >
   >要了解有关 **表单** 类型文件，请参阅 [本页](../../configuration/using/identifying-a-form.md).

   在本例中， **表单** 文件必须基于 **cus：单个** 架构，因此具有以下布局：

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

1. 转到 **[!UICONTROL Administration>Configuration>Navigation hierarchies]** 节点。
1. 新建 **xtk:navtree** type **navtree** 文档。
1. 根据表模板描述您需要的所有监视和字段。

   >[!NOTE]
   >
   >更多信息 **navtree** 类型文件，请参阅 [本页](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

   在当前示例中， **navtree** 文件必须基于 **cus：单个** 架构，因此具有以下形式：

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
