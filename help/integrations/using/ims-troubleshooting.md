---
product: campaign
title: IMS 故障排除
description: IMS 故障排除
feature: Configuration
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v7-prem: label="内部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 49271e291953483ee14709b26ec053217a336718
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 1%

---

# IMS 故障排除{#ims-troubleshooting}


以下故障诊断提示将有所帮助 **内部部署** 和 **混合** 客户可以解决使用IMS集成时最常见的问题。 对象 **托管** 客户，请联系Adobe。

**外部帐户**

只应 **一** 外部帐户，具有以下设置：

* **内部名称**：Adobe_Marketing_Cloud
* **类型**：Adobe Marketing Cloud

删除具有相同设置的任何重复外部帐户。

**产品上下文**

如果外部帐户具有 **产品上下文** 字段中，检查其值是否设置为： **dma_campaign_classic**

确保您的产品上下文与Campaign和Experience Cloud相同。

例如，如果 **产品上下文** 不会显示，默认产品上下文应为 **dma_campaign** 促销活动和Experience Cloud。 如果 **产品上下文** 字段，则默认产品上下文应为 **dma_campaign_classic** 促销活动和Experience Cloud。

**[!UICONTROL IMS Server URL]**

在营销活动中 **Adobe Marketing Cloud** 外部帐户，检查 **[!UICONTROL IMS Server URL]** 是 `adobeid-na1.services.adobe.com` 或 `ims-na1.adobelogin.com`. 确保暂存实例和生产实例都指向同一个IMS生产端点。

**关联掩码**

* 检查尝试登录的用户是否属于Enterprise Dashboard中的运算符组。
* 检查 **[!UICONTROL Association Mask]** 是Enterprise Dashboard中用户操作员组名称的前缀。
* 确保没有空格和拼写错误。
* 检查Campaign中操作员组的名称是否未更改，并遵循以下语法：

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**范围**

在Campaign外部帐户中定义的范围必须是IMS所设置的范围的子集。

**回调URL**

此 **回调URL** 列入允许列表应添加到并以“https://”开头。 检查 **回调URL** 链接到相应的实例。 例如，生产实例应重定向到生产URL。

**客户端ID和密码**

Campaign外部帐户与IMS设置的外部帐户之间的客户端ID匹配。

检查输入的客户端密码是否正确。

**重新启动服务器**

如果对Campaign外部帐户中的上述设置进行了任何更改，请重新启动服务器

**常见错误类型和可能的解决方案**

* 用户将被重定向至adobe.com页面：

  有一个问题 **[!UICONTROL Callback URL]**. 请参阅之前的步骤以检查 **[!UICONTROL Callback URL]** 配置。

* 消息“Login does not any right matching the expression”（登录没有任何权限与表达式匹配）：

  请参阅之前的步骤以检查 **[!UICONTROL Association Mask]** 和操作员组配置。

* 用户无法访问Adobe ID登录页面：

  请参阅前面的步骤以检查作用域配置。
