---
title: 向运营商发送个性化提醒
seo-title: 向运营商发送个性化提醒
description: 向运营商发送个性化提醒
seo-description: null
page-status-flag: never-activated
uuid: 10dd46b9-df28-4043-91f9-c9316a7c69d3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4d72db10-29bd-4b3c-adb3-bead02890271
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 5%

---


# 向运营商发送个性化提醒{#sending-personalized-alerts-to-operators}

在此示例中，我们希望向操作员发送警报，该操作员将包含打开新闻稿但未单击新闻稿所包含链接的用户档案的名称。

用户档案的名字和姓字段链接到 **[!UICONTROL Recipients]** 定位维度，而活动 **[!UICONTROL Alert]** 链接到定位维度 **[!UICONTROL Operator]** 。 因此，两个定位维度之间没有可用的字段来执行对帐和检索名字和姓氏字段，并在警报活动中显示它们。

该过程是按如下方式构建工作流：

1. 使用 **[!UICONTROL Query]** 活动目标数据。
1. 在工作流 **[!UICONTROL JavaScript code]** 中添加一个活动，将查询从填充保存到实例变量。
1. 使用 **[!UICONTROL Test]** 活动检查人口计数。
1. 根据 **[!UICONTROL Alert]** 活动结果，使用活动向操作员发送警 **[!UICONTROL Test]** 报。

![](assets/uc_operator_1.png)

## 将填充保存到实例变量 {#saving-the-population-to-the-instance-variable}

将下面的代码添加到 **[!UICONTROL JavaScript code]** 活动。

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

* 标 **[!UICONTROL queryDef schema]** 签应与在定位维度活动中使用的查询的名称相对应。
* 标 **[!UICONTROL node expr]** 记应与要检索的字段的名称相对应。

![](assets/uc_operator_3.png)

要检索这些信息，请按照以下步骤操作：

1. 从活动中右键单击出站过渡 **[!UICONTROL Query]** ，然后选择 **[!UICONTROL Display the target]**。

   ![](assets/uc_operator_4.png)

1. 右键单击列表，然后选择 **[!UICONTROL Configure list]**。

   ![](assets/uc_operator_5.png)

1. 查询定位维度和字段名称显示在列表中。

   ![](assets/uc_operator_6.png)

## 测试人口数 {#testing-the-population-count}

将下面的代码添加到 **[!UICONTROL Test]** 活动中，以检查目标人群是否至少包含1个用户档案。

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## 设置警报 {#setting-up-the-alert}

现在，已将填充添加到具有所需字段的实例变量中，您可以将这些信息添加到 **[!UICONTROL Alert]** 活动。

为此，请在选项卡中 **[!UICONTROL Source]** 添加以下代码：

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
>该 **[!UICONTROL <%= item.target.recipient.@fieldName %>]** 命令允许您通过活动向实例变量添加已保存的字段之 **[!UICONTROL JavaScript code]** 一。\
>只要字段已插入到JavaScript代码中，就可以添加所需数量的字段。

![](assets/uc_operator_8.png)

