---
product: campaign
title: 新建字段向导
description: 新建字段向导
feature: Schema Extension
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 4%

---

# 新建字段向导{#new-field-wizard}

![](../../assets/v7-only.svg)

可通过访问的向导 **[!UICONTROL Tools > Advanced > Add new fields]** 用于向数据库中的表添加一个或多个字段。

验证向导会更新要扩展的表的扩展模式，并启动SQL脚本以修改数据库的物理结构。

该助手具有快速添加字段而无需了解数据模式的结构的优点。

主要缺点是数据和属性的限制。

向导屏幕包含以下步骤：

1. 在第一页中，您可以输入要扩展的架构的名称以及将在其中保存修改的扩展架构的命名空间：

   ![](assets/d_ncs_integration_schema_addfield.png)

1. 在下一页中，您可以输入要添加的字段的属性。

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. 要确认更改，请单击 **[!UICONTROL Finish]** 按钮。

将自动创建名为“cus:recipient”的扩展文件，并执行相应的SQL脚本：

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>默认情况下，添加的字段将使用属性声明 **用户** （具有值“true”）。 这允许您使用“treeEdit”类型控件（请参阅输入表单）在扩展架构的输入表单中显示和编辑字段。
