---
product: campaign
title: 关于 Adobe Experience Cloud 触发器
description: Adobe Experience Cloud Triggers实施入门
feature: Triggers
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 7%

---

# 使用Campaign和Experience Cloud触发器{#about-adobe-experience-triggers}

[!DNL Triggers]是使用管道的Adobe Campaign和Adobe Analytics之间的集成。 管道从您的网站检索用户的操作或触发器。 放弃购物车就是一个触发器示例。 在Adobe Campaign中处理触发器，以近乎实时地发送电子邮件。

>[!CAUTION]
>
>此功能并非作为产品的一部分现成可用。对于此实施，请与您的Adobe代表/客户关怀团队合作。 然后，您将能够执行此[页面](../../integrations/using/configuring-pipeline.md#prerequisites)中详述的步骤。

[!DNL Triggers]在用户操作后的短时间内运行营销操作。 典型响应时间不到一小时。

由于配置很少且没有第三方参与，因此它允许更敏捷的集成。
它还支持高流量而不影响营销活动的性能。 例如，集成每小时可处理100万个触发器。

![](assets/do-not-localize/book.png)了解如何[创建Experience Cloud触发器](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html)，识别、定义并监视关键客户行为。

## [!DNL Triggers]架构 {#triggers-architecture}

[!DNL pipelined]进程始终在Adobe Campaign营销服务器上运行。 它连接到管道，检索事件，并立即处理它们。

![](assets/triggers_2.png)

[!DNL pipelined]进程使用身份验证服务登录到Experience Cloud并发送私钥。 身份验证服务返回一个令牌。 令牌用于在检索事件时进行身份验证。

## 先决条件 {#adobe-io-prerequisites}

在开始此实施之前，请检查您是否拥有：

* 有效的&#x200B;**组织标识符**：组织ID是Adobe Experience Cloud中的唯一标识符，用于VisitorID服务和IMS单点登录(SSO)。 [了解详情](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-hans)
* 您组织的&#x200B;**开发人员访问权限**。 组织的系统管理员需要遵循此页面](https://helpx.adobe.com/enterprise/using/manage-developers.html)中详细的[的&#x200B;**将开发人员添加到单个产品配置文件**&#x200B;过程，以便为与触发器关联的Adobe Analytics产品的`Analytics - {tenantID}`产品配置文件提供开发人员访问权限。

## 实施步骤 {#implement}

要实施Campaign和Experience Cloud Triggers，请执行以下步骤：

1. 创建OAuth项目。 [了解详情](oauth-technical-account.md#oauth-service)

1. 在Adobe Campaign中添加您的OAuth项目凭据。 [了解详情](oauth-technical-account.md#add-credentials)

1. 按如下所示将身份验证类型更新到配置文件&#x200B;**config-&lt; instance-name >.xml**&#x200B;中的开发人员控制台项目：

   ```
   <pipelined ... authType="imsJwtToken"  ... />
   ```

   然后，运行`config -reload`并重新启动[!DNL pipelined]以考虑更改。

