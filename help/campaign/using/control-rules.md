---
title: 控制规则
seo-title: 控制规则
description: 控制规则
seo-description: null
page-status-flag: never-activated
uuid: a83e56d0-573a-4592-b2b1-0d3b3e52b03f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: be037a80-3f94-465c-ba7d-ae7d50f70e36
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 3%

---


# 控制规则{#control-rules}

## 分析和仲裁控制规则 {#analysis-and-arbitration-control-rules}

通过控制规则，您可以在投放之前保证消息的有效性和质量：字符显示、SMS大小、地址格式等。

一套现成的规则允许您执行常规检查。 这些检查（在界面中以粗体显示）包括：

* **[!UICONTROL Object approval]** （电子邮件）:检查发送方对象和地址是否不包含可能导致某些邮件代理出现问题的特殊字符。
* **[!UICONTROL URL label approval]** （电子邮件）:检查每个跟踪URL是否都有标签。
* **[!UICONTROL URL approval]** （电子邮件）:检查跟踪URL（存在“&amp;”字符）。
* **[!UICONTROL Message size approval]** （移动）:检查短信的大小。
* **[!UICONTROL Validity period check]** （电子邮件）:检查投放的有效期是否长到足以发送所有消息。
* **[!UICONTROL Proof size check]** (所有渠道):如果验证目标总数超过100个收件人，则生成错误消息。
* **[!UICONTROL Wave scheduling check]** （电子邮件）:检查如果投放被分解为多个批次，则最后一波开始是否计划在有效期结束之前进行投放。
* **[!UICONTROL Unsubscription link approval]** （电子邮件）:检查每个内容（HTML和文本）中是否存在至少一个退订（选择退出）URL。

## Creating a control rule {#creating-a-control-rule}

可以创建新的控制规则以满足您的需求。 为此，请创建一个 **[!UICONTROL Control]** 类型规则，并在选项卡的SQL中输入控制 **[!UICONTROL Code]** 公式。

**示例:**

在以下示例中，我们将创建一个规则来防止SMS优惠被发送到100多个收件人。 此规则将链接到活动类型，然后链接到相关优惠可用的SMS投放。

应用以下步骤：

1. 创建 **[!UICONTROL Control]** 类型规则 选择警 **[!UICONTROL Warning]** 报级别。

   ![](assets/campaign_opt_create_control_01.png)

1. 在选项卡 **[!UICONTROL Code]** 中，输入要应用所需阈值的脚本，如下所示：

   ![](assets/campaign_opt_create_control_02.png)

   如果投放目标超过100个联系人，此脚本将触发警告：

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. 将此规则链接到活动类型，并参考相关SMS投放中的类型。

   ![](assets/campaign_opt_create_control_03.png)

1. 在投放分析期间，将应用规则并创建警告（如果适用）。

   ![](assets/campaign_opt_create_control_04.png)

   但是，投放仍可以发送。

   如果提高警报级别，将阻止投放启动。

   ![](assets/campaign_opt_create_control_05.png)

   在分析结束时，该 **[!UICONTROL Confirm delivery]** 按钮将不可用。

   ![](assets/campaign_opt_create_control_06.png)

