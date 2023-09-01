---
product: campaign
title: 新建字段向导
description: 新建字段向导
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Schema Extension
role: Data Engineer, Developer
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 7%

---

# 新建字段向导{#new-field-wizard}


可通过访问的向导 **[!UICONTROL Tools > Advanced > Add new fields]** 用于向数据库中的表添加一个或多个字段。

验证向导将更新要扩展的表的扩展模式，并启动SQL脚本以修改数据库的物理结构。

该助理具有无需了解数据模式的结构即可快速添加字段的优势。

主要缺点是数据的局限性和需要扩展的特性。

向导屏幕包含以下步骤：

1. 在第一个页面中，您可以输入要扩展的架构的名称以及保存修改的扩展架构的命名空间：

   ![](assets/d_ncs_integration_schema_addfield.png)

1. 在下一页中，您可以输入要添加的字段的属性。

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. 要确认更改，请单击 **[!UICONTROL Finish]** 按钮。

在本例中，我们将自动创建一个名为“cus：recipient”的扩展文件，并执行相应的SQL脚本：

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>默认情况下，添加的字段使用属性声明 **用户** （值为“true”）。 这使您可以使用“treeEdit”类型的控件（请参阅输入表单）在扩展架构的输入表单中显示和编辑字段。
