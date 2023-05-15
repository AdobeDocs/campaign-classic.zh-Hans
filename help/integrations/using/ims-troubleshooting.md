---
product: campaign
title: IMS 故障排除
description: IMS 故障排除
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: 1ce89c3a-1fe6-4ed6-9547-2eb9713a0ec3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---

# IMS 故障排除{#ims-troubleshooting}



以下故障诊断提示将提供帮助 **内部部署** 客户可解决使用IMS集成时出现的最常见问题。 对于 **托管** 客户，请联系Adobe。

**外部帐户**

应该只有 **one** 具有以下设置的外部帐户：

* **内部名称**:Adobe_Marketing_Cloud
* **类型**:Adobe Marketing Cloud

删除具有相同设置的任何重复的外部帐户。

**产品上下文**

如果外部帐户具有 **产品上下文** 字段，检查其值设置为： **dma_campaign_classic**

确保Campaign和Experience Cloud的产品上下文相同。

例如，如果 **产品上下文** 未显示，则默认的产品上下文应为 **dma_campaign** 在Campaign和Experience Cloud中。 如果 **产品上下文** 字段中，默认的产品上下文应为 **dma_campaign_classic** 在Campaign和Experience Cloud中。

**[!UICONTROL IMS Server URL]**

在营销活动中 **Adobe Marketing Cloud** 外部帐户，检查 **[!UICONTROL IMS Server URL]** 是 `adobeid-na1.services.adobe.com` 或 `ims-na1.adobelogin.com`. 确保暂存实例和生产实例指向相同的IMS生产端点。

**关联掩码**

* 检查尝试登录的用户是否属于Enterprise Dashboard中的操作员组。
* 检查 **[!UICONTROL Association Mask]** 是Enterprise Dashboard中用户操作员组名称的前缀。
* 确保没有空格和拼写错误。
* 检查Campaign中运算符组的名称是否未更改，并遵循以下语法：

```
<Association Mask> + <Operator Group Name in Campaign> = Complete name of the operator group in Enterprise Dashboard
```

**范围**

Campaign外部帐户中定义的范围必须是IMS设置的范围的子集。

**回调URL**

的 **回调URL** 应添加到允许列表，并以“https://”开头。 检查 **回调URL** 链接到相应的实例。 例如，生产实例应重定向到生产URL。

**客户端ID和密钥**

客户ID在Campaign外部帐户和IMS设置的帐户之间匹配。

检查输入的客户端密钥是否正确。

**重新启动服务器**

如果对Campaign外部帐户中的上述设置进行了任何更改，请重新启动服务器

**常见的错误类型和可能的解决方案**

* 用户将被重定向到adobe.com页面：

   在 **[!UICONTROL Callback URL]**. 请参阅上述步骤，以检查 **[!UICONTROL Callback URL]** 配置。

* 消息“登录没有任何与表达式匹配的权限”：

   请参阅上述步骤，以检查 **[!UICONTROL Association Mask]** 和运算符组配置。

* 用户无法访问Adobe ID登录页面：

   请参阅上述步骤以检查范围配置。
