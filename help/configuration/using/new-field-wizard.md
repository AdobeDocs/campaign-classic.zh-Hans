---
title: 新建字段向导
seo-title: 新建字段向导
description: 新建字段向导
seo-description: null
page-status-flag: never-activated
uuid: 2c8d35db-042a-47cf-a7a6-3bb63bf40d94
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6da65fb5-18a1-41a0-96d8-588e383f944b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 新建字段向导{#new-field-wizard}

通过可访问的向 **[!UICONTROL Tools > Advanced > Add new fields]** 导可向数据库中的表添加一个或多个字段。

验证向导将更新要扩展的表的扩展架构，并启动SQL脚本以修改数据库的物理结构。

该助手具有无需了解数据架构结构即可快速添加字段的优点。

主要的缺点是数据和属性的限制。

向导屏幕包含以下步骤：

1. 在第一页中，您可以输入要扩展的架构的名称以及将在其中保存修改的扩展架构的命名空间：

   ![](assets/d_ncs_integration_schema_addfield.png)

1. 在下一页中，您可以输入要添加的字段的属性。

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. 要确认更改，请单击 **[!UICONTROL Finish]** 按钮。

我们的示例中名为“cus:recipient”的扩展文件将自动创建并执行相应的SQL脚本：

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>默认情况下，添加的字段使用属性 **用户** （值为“true”）声明。 这允许您使用“treeEdit”类型控件（请参阅输入表单）在扩展架构的输入表单中显示和编辑字段。

