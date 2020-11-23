---
solution: Campaign Classic
product: campaign
title: IMS 疑难解答
description: IMS 疑难解答
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 1%

---


# IMS 疑难解答{#ims-troubleshooting}

以下故障排除提示将帮 **助预置型** 客户解决使用IMS集成时出现的最常见问题。 对于托 **管客户** ，请与Adobe联系。

**外部帐户**

只应有一 **个外部帐户** ，并且设置如下：

* **内部名称**:Adobe_Marketing_Cloud
* **类型**:Adobe Marketing Cloud

删除具有相同设置的任何重复外部帐户。

**产品上下文**

如果外部帐户有“ **产品上下文** ”字段，请检查其值是否设置为： **dma_活动_classic**

确保您的产品上下文对于活动和Experience Cloud相同。

例如，如果未显 **示Product** Context **，则默认的product context应同时** 采用活动和Experience Cloud。 如果出 **现“Product Context** （产品上下文）”字段 **，则默认产品上下文应** 在活动和Experience Cloud中均为dma_活动_classic。

**[!UICONTROL IMS Server URL]**

在活动 **Adobe Marketing Cloud** 外部帐户中，检 **[!UICONTROL IMS Server URL]** 查是 [adobeid-na1.services.adobe.com还是ims](https://adobeid-na1.services.adobe.com/) -na1 [.adobelogin.com](http://ims-na1.adobelogin.com/)。 确保舞台和生产实例指向同一IMS生产端点。

**关联掩码**

* 检查尝试登录的用户是否属于企业仪表板中的操作员组。
* 检查该 **[!UICONTROL Association Mask]** 是“企业”仪表板中用户的操作员组名称的前缀。
* 确保没有空白和拼写错误。
* 检查活动中运算符组的名称是否未更改，并遵循以下语法：

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**范围**

活动外部帐户中定义的范围必须是IMS提供的范围的子集。

**回调URL**

回 **** 调URL应添允许列表加到开始和(带有“https://”)。 检查回 **调URL** 是否已链接到相应实例。 例如，生产实例应重定向到生产URL。

**客户端ID和机密**

活动外部帐户与IMS提供的客户端ID匹配。

检查输入的客户端机密是否正确。

**重新启动服务器**

如果在活动外部帐户中对上述设置进行了任何更改，请重新启动服务器

**常见错误类型和可能的解决方案**

* 用户被重定向到adobe.com页面：

   这有问题 **[!UICONTROL Callback URL]**。 请参阅上述步骤以检查配 **[!UICONTROL Callback URL]** 置。

* 消息“登录名没有与表达式匹配的任何权利”:

   请参阅上述步骤以检查和运 **[!UICONTROL Association Mask]** 算符组配置。

* 用户无法访问Adobe ID登录页面：

   请参阅上述步骤以检查范围配置。

