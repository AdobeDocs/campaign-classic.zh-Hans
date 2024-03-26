---
product: campaign
title: 向操作员发送个性化提醒
description: 了解如何向运营商发送个性化提醒
badge-v7-only: label="v7" type="Informative" tooltip="仅适用于 Campaign Classic v7"
feature: Workflows
exl-id: 21c97eb3-60cd-4d19-bc0f-5ba9ec17e70a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 4%

---

# 向操作员发送个性化提醒{#sending-personalized-alerts-to-operators}



在本例中，我们希望向操作员发送警报，该警报将包含打开了新闻稿但未单击新闻稿所包含链接的用户档案名称。

用户档案的名字和姓氏字段链接到 **[!UICONTROL Recipients]** 定位维度，而 **[!UICONTROL Alert]** 活动链接到 **[!UICONTROL Operator]** 定位维度。 因此，两个定向维度之间没有可用的字段来执行协调，检索名字和姓氏字段并在警报活动中显示它们。

该过程将构建一个工作流，如下所示：

1. 使用 **[!UICONTROL Query]** 活动，以定位数据。
1. 添加 **[!UICONTROL JavaScript code]** 活动添加到工作流中，以将查询中的群体保存到实例变量。
1. 使用 **[!UICONTROL Test]** 用于检查群体计数的活动。
1. 使用 **[!UICONTROL Alert]** 活动，向操作员发送警报，具体取决于 **[!UICONTROL Test]** 活动结果。

![](assets/uc_operator_1.png)

## 将群体保存到实例变量 {#saving-the-population-to-the-instance-variable}

将以下代码添加到 **[!UICONTROL JavaScript code]** 活动。

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

* 此 **[!UICONTROL queryDef schema]** 标记应与查询活动中使用的定向维度的名称相对应。
* 此 **[!UICONTROL node expr]** 标记应该与要检索的字段的名称相对应。

![](assets/uc_operator_3.png)

要检索这些信息，请执行以下步骤：

1. 从右键单击叫客过渡 **[!UICONTROL Query]** 活动，然后选择 **[!UICONTROL Display the target]**.

   ![](assets/uc_operator_4.png)

1. 右键单击列表，然后选择 **[!UICONTROL Configure list]**.

   ![](assets/uc_operator_5.png)

1. 查询定向维度和字段名称显示在列表中。

   ![](assets/uc_operator_6.png)

## 测试群体计数 {#testing-the-population-count}

将以下代码添加到 **[!UICONTROL Test]** 活动以检查目标群体是否至少包含1个用户档案。

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## 设置警报 {#setting-up-the-alert}

现在，群体已使用所需字段添加到实例变量中，接下来您可以将这些信息添加到 **[!UICONTROL Alert]** 活动。

为此，请将添加到 **[!UICONTROL Source]** 选项卡下面的代码：

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
>此 **[!UICONTROL <%= item.target.recipient.@fieldName %>]** 命令允许您添加已通过保存到实例变量的字段之一 **[!UICONTROL JavaScript code]** 活动。\
>您可以根据需要添加任意数量的字段，只要这些字段已插入JavaScript代码中即可。

![](assets/uc_operator_8.png)
