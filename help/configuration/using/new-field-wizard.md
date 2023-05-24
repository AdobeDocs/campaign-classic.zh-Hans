---
product: campaign
title: 新建字段向导
description: 新建字段向导
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Schema Extension
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 4%

---

# 新建字段向导{#new-field-wizard}


可通过以下方式访问的向导 **[!UICONTROL Tools > Advanced > Add new fields]** 用于向数据库中的表添加一个或多个字段。

验证向导将更新要扩展的表的扩展模式，并启动SQL脚本以修改数据库的物理结构。

该助理具有无需了解数据模式的结构即可快速添加字段的优势。

主要缺点是数据有限和属性有待扩展。

向导屏幕包含以下步骤：

1. 在第一个页面中，您可以输入要扩展的架构的名称以及保存修改的扩展架构的命名空间：

   ![](assets/d_ncs_integration_schema_addfield.png)

1. 在下一页中，您可以输入要添加的字段的属性。

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. 要确认更改，请单击 **[!UICONTROL Finish]** 按钮。

在本例中，名为“cus：recipient”的扩展文件是自动创建的，并会执行相应的SQL脚本：

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>默认情况下，使用属性声明添加的字段 **用户** （值为“true”）。 这样，您就可以使用“treeEdit”类型的控件（请参阅输入表单）显示和编辑扩展架构输入表单中的字段。
