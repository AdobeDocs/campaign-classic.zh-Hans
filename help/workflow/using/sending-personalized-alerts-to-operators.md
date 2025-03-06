---
product: campaign
title: 向操作员发送个性化提醒
description: 了解如何向运营商发送个性化提醒
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 21c97eb3-60cd-4d19-bc0f-5ba9ec17e70a
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 2%

---

# 向操作员发送个性化提醒{#sending-personalized-alerts-to-operators}



在本例中，我们希望向操作员发送警报，该警报将包含打开了新闻稿但未单击新闻稿所包含链接的用户档案名称。

用户档案的名字和姓氏字段链接到&#x200B;**[!UICONTROL Recipients]**&#x200B;定向维度，而&#x200B;**[!UICONTROL Alert]**&#x200B;活动链接到&#x200B;**[!UICONTROL Operator]**&#x200B;定向维度。 因此，两个定向维度之间没有可用的字段来执行协调，检索名字和姓氏字段并在警报活动中显示它们。

该过程将构建一个工作流，如下所示：

1. 使用&#x200B;**[!UICONTROL Query]**&#x200B;活动来定位数据。
1. 将&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动添加到工作流中，以将查询的填充保存到实例变量。
1. 使用&#x200B;**[!UICONTROL Test]**&#x200B;活动检查群体计数。
1. 根据&#x200B;**[!UICONTROL Test]**&#x200B;活动结果，使用&#x200B;**[!UICONTROL Alert]**&#x200B;活动向操作员发送警报。

![](assets/uc_operator_1.png)

## 将群体保存到实例变量 {#saving-the-population-to-the-instance-variable}

将以下代码添加到&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动中。

```
var query = xtk.queryDef.create(  
    <queryDef schema="temp:query" operation="select">  
      <select>  
       <node expr="[target/recipient.@firstName]"/>  
       <node expr="[target/recipient.@lastName]"/>  
      </select>  
     </queryDef>  
  );  
  var items = query.ExecuteQuery();
```

确保Javascript代码与您的工作流信息相对应：

* **[!UICONTROL queryDef schema]**&#x200B;标记应该与查询活动中使用的定向维度的名称相对应。
* **[!UICONTROL node expr]**&#x200B;标记应该与要检索的字段的名称相对应。

![](assets/uc_operator_3.png)

要检索这些信息，请执行以下步骤：

1. 右键单击&#x200B;**[!UICONTROL Query]**&#x200B;活动中的叫客过渡，然后选择&#x200B;**[!UICONTROL Display the target]**。

   ![](assets/uc_operator_4.png)

1. 右键单击列表，然后选择&#x200B;**[!UICONTROL Configure list]**。

   ![](assets/uc_operator_5.png)

1. 查询定向维度和字段名称显示在列表中。

   ![](assets/uc_operator_6.png)

## 测试群体计数 {#testing-the-population-count}

将以下代码添加到&#x200B;**[!UICONTROL Test]**&#x200B;活动中以检查目标群体是否至少包含1个配置文件。

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## 设置警报 {#setting-up-the-alert}

现在，群体已使用所需字段添加到实例变量中，您可以将这些信息添加到&#x200B;**[!UICONTROL Alert]**&#x200B;活动中。

为此，请将以下代码添加到&#x200B;**[!UICONTROL Source]**&#x200B;选项卡中：

```
<ul>
<%
var items = new XML(instance.vars.items)
for each (var item in items){
%>
<li><%= item.target.@firstName %> <%= item.target.@lastName %></li>
<%
} %></ul>
```

>[!NOTE]
>
>**[!UICONTROL <%= item.target.recipient.@fieldName %>]**&#x200B;命令允许您添加通过&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活动保存到实例变量的字段之一。\
>您可以根据需要添加任意数量的字段，但前提是这些字段已插入JavaScript代码中。

![](assets/uc_operator_8.png)
