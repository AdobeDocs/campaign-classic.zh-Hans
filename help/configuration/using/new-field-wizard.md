---
solution: Campaign Classic
product: campaign
title: 新建字段向导
description: 新建字段向导
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 4%

---


# 新建字段向导{#new-field-wizard}

通过可访问的 **[!UICONTROL Tools > Advanced > Add new fields]** 向导，可向数据库的表中添加一个或多个字段。

验证向导将更新要扩展的表的扩展模式，并启动SQL脚本以修改数据库的物理结构。

该助手具有无需了解数据模式结构即可快速添加字段的优点。

主要缺点是数据和属性的限制。

向导屏幕包含以下步骤：

1. 在第一页中，您可以输入要扩展的模式的名称以及要保存修改的扩展模式的命名空间:

   ![](assets/d_ncs_integration_schema_addfield.png)

1. 在下一页中，您可以输入要添加的字段的属性。

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. 要确认更改，请单击 **[!UICONTROL Finish]** 按钮。

我们的示例中名为“cus:收件人”的扩展文件将自动创建并执行相应的SQL脚本：

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>默认情况下，添加的字段使用属性 **用户** （值为“true”）声明。 这允许您使用“treeEdit”类型的控件（请参阅输入表单）在扩展模式的输入表单中显示和编辑字段。

