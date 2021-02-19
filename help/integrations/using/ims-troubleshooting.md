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

以下故障排除技巧将帮助&#x200B;**内部部署**&#x200B;客户解决使用IMS集成时出现的最常见问题。 对于&#x200B;**托管的**&#x200B;客户，请联系Adobe。

**外部帐户**

只应具有以下设置的&#x200B;**一个**&#x200B;外部帐户:

* **内部名称**:Adobe_Marketing_Cloud
* **类型**:Adobe Marketing Cloud

删除设置相同的任何重复外部帐户。

**Product Context**

如果外部帐户有&#x200B;**Product Context**&#x200B;字段，请检查其值是否设置为：**dma_活动_classic**

确保您的产品上下文与活动和Experience Cloud相同。

例如，如果未显示&#x200B;**产品上下文**，则默认产品上下文应为&#x200B;**dma_活动**(在活动和Experience Cloud中)。 如果出现&#x200B;**Product Context**&#x200B;字段，则默认产品上下文应为&#x200B;**dma_活动_classic**(在活动和Experience Cloud中)。

**[!UICONTROL IMS Server URL]**

在活动&#x200B;**Adobe Marketing Cloud**&#x200B;外部帐户中，检查&#x200B;**[!UICONTROL IMS Server URL]**&#x200B;是[adobeid-na1.services.adobe.com](https://adobeid-na1.services.adobe.com/)还是[ims-na1.adobelogin.com](http://ims-na1.adobelogin.com/)。 确保舞台和生产实例指向同一IMS生产端点。

**关联蒙版**

* 检查尝试登录的用户是否属于“企业”仪表板中的操作员组。
* 检查&#x200B;**[!UICONTROL Association Mask]**&#x200B;是否是“企业”仪表板中用户操作符组名称的前缀。
* 确保没有空白和拼写错误。
* 检查活动中运算符组的名称是否未更改，并遵循以下语法：

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**范围**

在活动外部帐户中定义的作用域必须是IMS提供的作用域的子集。

**回调URL**

应将&#x200B;**回调URL**&#x200B;添加到带有“允许列表https://”的开始和。 检查&#x200B;**回调URL**&#x200B;是否链接到相应实例。 例如，生产实例应重定向到生产URL。

**客户端ID和密钥**

客户端ID在活动外部帐户和IMS提供的客户端ID之间匹配。

检查输入的客户端机密是否正确。

**重新启动服务器**

如果在活动外部帐户中对上述设置进行了任何更改，请重新启动服务器

**常见错误类型和可能的解决方案**

* 用户被重定向到adobe.com页面：

   **[!UICONTROL Callback URL]**&#x200B;有问题。 请参阅上述步骤以检查&#x200B;**[!UICONTROL Callback URL]**&#x200B;配置。

* 消息“登录名没有与表达式匹配的任何权利”：

   请参阅上述步骤以检查&#x200B;**[!UICONTROL Association Mask]**&#x200B;和运算符组配置。

* 用户无法访问Adobe ID登录页面：

   请参阅上述步骤以检查范围配置。

