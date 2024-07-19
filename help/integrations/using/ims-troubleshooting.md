---
product: campaign
title: IMS 故障排除
description: IMS 故障排除
feature: Configuration
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# IMS 故障排除{#ims-troubleshooting}


以下疑难解答提示将帮助&#x200B;**内部部署**&#x200B;和&#x200B;**混合**&#x200B;客户解决使用IMS集成时最常见的问题。 对于&#x200B;**托管**&#x200B;客户，请联系Adobe。

**外部帐户**

应该只存在具有以下设置的&#x200B;**一个**&#x200B;外部帐户：

* **内部名称**：Adobe_Marketing_Cloud
* **类型**： Adobe Marketing Cloud

删除具有相同设置的任何重复外部帐户。

**产品上下文**

如果外部帐户具有&#x200B;**产品上下文**&#x200B;字段，请检查其值是否设置为： **dma_campaign_classic**

确保您的产品上下文与Campaign和Experience Cloud相同。

例如，如果未显示&#x200B;**产品上下文**，则促销活动和Experience Cloud中的默认产品上下文都应是&#x200B;**dma_campaign**。 如果出现&#x200B;**产品上下文**&#x200B;字段，则促销活动和Experience Cloud中的默认产品上下文都应是&#x200B;**dma_campaign_classic**。

**[!UICONTROL IMS Server URL]**

在营销活动&#x200B;**Adobe Marketing Cloud**&#x200B;外部帐户中，检查&#x200B;**[!UICONTROL IMS Server URL]**&#x200B;是`adobeid-na1.services.adobe.com`还是`ims-na1.adobelogin.com`。 确保暂存实例和生产实例都指向同一个IMS生产端点。

**关联掩码**

* 检查尝试登录的用户是否属于Enterprise Dashboard中的运算符组。
* 检查&#x200B;**[!UICONTROL Association Mask]**&#x200B;是否为Enterprise Dashboard中用户操作员组名称的前缀。
* 确保没有空格和拼写错误。
* 检查Campaign中操作员组的名称是否未更改，并遵循以下语法：

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**作用域**

在Campaign外部帐户中定义的范围必须是IMS所设置的范围的子集。

**回调URL**

列入允许列表 **回调URL**&#x200B;应添加到并以“https://”开头。 检查&#x200B;**回调URL**&#x200B;是否链接到相应的实例。 例如，生产实例应重定向到生产URL。

**客户端ID和密码**

Campaign外部帐户与IMS设置的外部帐户之间的客户端ID匹配。

检查输入的客户端密码是否正确。

**重新启动服务器**

如果对Campaign外部帐户中的上述设置进行了任何更改，请重新启动服务器

**常见错误类型和可能的解决方案**

* 用户将被重定向至adobe.com页面：

  **[!UICONTROL Callback URL]**&#x200B;有问题。 请参阅之前的步骤以检查&#x200B;**[!UICONTROL Callback URL]**&#x200B;配置。

* 消息“Login does not any right matching the expression”（登录没有任何权限与表达式匹配）：

  请参阅前面的步骤以检查&#x200B;**[!UICONTROL Association Mask]**&#x200B;和操作员组的配置。

* 用户无法访问Adobe ID登录页面：

  请参阅前面的步骤以检查作用域配置。
