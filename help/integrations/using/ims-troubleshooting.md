---
title: IMS疑难解答
seo-title: IMS疑难解答
description: IMS疑难解答
seo-description: null
page-status-flag: never-activated
uuid: 5db95afc-8cbf-4ec3-b58f-504486fe4a40
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
discoiquuid: e31db11a-ad8e-4fd0-bab7-0df1079231c9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0745b9c9d72538b8573ad18ff4054ecf788905f2

---


# IMS疑难解答{#ims-troubleshooting}

以下疑难解答提示将帮 **助内部客户解决** IMS集成中最常见的问题。 对于托 **管客户** ，请联系Adobe。

**外部帐户**

只应有一个 **具有** 以下设置的外部帐户：

* **内部名称**:Adobe_Marketing_Cloud
* **类型**:Adobe Marketing Cloud

删除具有相同设置的任何重复外部帐户。

**Product Context**

如果外部帐户有“ **Product Context** ”字段，请检查其值是否设置为： **dma_campaign_classic**

确保您的产品上下文与Campaign和Experience cloud的上下文相同。

例如，如果未显 **示产品上下文** ，则默认产品上下文应为 **dma_campaign** ，同时位于Campaign和Experience Cloud中。 如果显 **示“产品上下文** ”字段，则默认的产品上下文应为 **dma_campaign_classic** ，在Campaign和Experience cloud中均是如此。

**[!UICONTROL IMS Server URL]**

在Campaign **Adobe Marketing cloud外部帐户中，检查** 是 **[!UICONTROL IMS Server URL]** adobeid-na1.services.adobe.com还是 [ims-na1.adobelogin.com](https://adobeid-na1.services.adobe.com/)[](http://ims-na1.adobelogin.com/)。 确保舞台和生产实例都指向同一个IMS生产端点。

**关联蒙版**

* 检查尝试登录的用户是否属于Enterprise Dashboard中的操作员组。
* 在Enterprise Dashboard **[!UICONTROL Association Mask]** 中，检查该用户的操作员组名称的前缀。
* 确保没有空格和拼写错误。
* 检查Campaign中运算符组的名称是否未更改，并遵循以下语法：

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**范围**

营销活动外部帐户中定义的范围必须是IMS提供的范围的子集。

**回调URL**

回 **调URL应列入白名单** ，并以“https://”开头。 检查回 **调URL** 是否已链接到相应的实例。 例如，生产实例应重定向到生产URL。

**客户端ID和机密**

客户端ID在Campaign外部帐户和IMS提供的帐户之间匹配。

检查输入的客户端机密是否正确。

**重新启动服务器**

如果对Campaign外部帐户中的上述设置进行了任何更改，请重新启动服务器

**常见的错误类型和可能的解决方案**

* 用户被重定向到adobe.com页面：

   问题在于 **[!UICONTROL Callback URL]**。 请参阅上述步骤以检查配 **[!UICONTROL Callback URL]** 置。

* 消息“登录没有与表达式匹配的任何权限”:

   请参阅上述步骤以检查和运 **[!UICONTROL Association Mask]** 算符组配置。

* 用户无法访问Adobe ID登录页：

   请参阅上述步骤以检查范围配置。

