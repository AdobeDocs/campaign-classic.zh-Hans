---
product: campaign
title: 新的外地助理
description: 新的外地助理
feature: Schema Extension
role: Data Engineer, Developer
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: ec774cc10a69a694b3c2bf5a6f662afd12a1435a
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# 新的外地助理{#new-field-wizard}


通过&#x200B;**[!UICONTROL Tools > Advanced > Add new fields]**&#x200B;可访问的助理允许您向数据库中的表添加一个或多个字段。

验证该助手将更新要扩展的表的扩展模式，并启动SQL脚本以修改数据库的物理结构。

该助理具有无需了解数据模式的结构即可快速添加字段的优势。

主要缺点是数据的局限性和需要扩展的特性。

助理屏幕包含以下步骤：

1. 在第一个页面中，您可以输入要扩展的架构的名称以及保存修改的扩展架构的命名空间：

   ![](assets/d_ncs_integration_schema_addfield.png)

1. 在下一页中，您可以输入要添加的字段的属性。

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. 要确认更改，请单击&#x200B;**[!UICONTROL Finish]**&#x200B;按钮。

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
>默认情况下，添加的字段声明为属性&#x200B;**user**（值为“true”）。 这使您可以使用“treeEdit”类型的控件（请参阅输入表单）在扩展架构的输入表单中显示和编辑字段。
