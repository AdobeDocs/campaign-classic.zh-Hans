---
product: campaign
title: 控制规则
description: 控制规则
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: 5a5f26f6-38da-4488-aadb-81fcb5359331
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 3%

---

# 控制规则{#control-rules}

![](../../assets/v7-only.svg)

## 分析和仲裁控制规则 {#analysis-and-arbitration-control-rules}

通过控制规则，您可以在投放之前保证消息的有效性和质量：字符显示、短信大小、地址格式等。

一组现成的规则允许您执行常规检查。 这些检查（在界面中以粗体显示）包括：

* **[!UICONTROL Object approval]** （电子邮件）：检查发件人对象和地址是否不包含可能导致某些邮件代理出现问题的特殊字符。
* **[!UICONTROL URL label approval]** （电子邮件）：检查每个跟踪URL是否具有标签。
* **[!UICONTROL URL approval]** （电子邮件）：检查跟踪URL（存在“&amp;”字符）。
* **[!UICONTROL Message size approval]** （移动设备）：检查短信消息的大小。
* **[!UICONTROL Validity period check]** （电子邮件）：检查投放的有效期是否足够长以发送所有消息。
* **[!UICONTROL Proof size check]** （所有渠道）：如果校样目标群体超过100个收件人，则会生成错误消息。
* **[!UICONTROL Wave scheduling check]** （电子邮件）：检查如果投放被划分为多个批次，则最后一波投放是否计划在有效期结束前开始。
* **[!UICONTROL Unsubscription link approval]** （电子邮件）：检查每个内容（HTML和文本）中是否至少有一个退订（选择退订）URL。

## 创建控制规则 {#creating-a-control-rule}

可以创建新的控制规则以满足您的需求。 为此，请创建&#x200B;**[!UICONTROL Control]**&#x200B;分类规则，并在&#x200B;**[!UICONTROL Code]**&#x200B;选项卡的SQL中输入控制公式。

**示例:**

在以下示例中，我们将创建一个规则，以阻止将短信选件发送到100多个收件人。 此规则将链接到营销活动分类，然后链接到相关选件可用的短信投放。

应用以下步骤：

1. 创建&#x200B;**[!UICONTROL Control]**&#x200B;分类规则。 选择&#x200B;**[!UICONTROL Warning]**&#x200B;警报级别。

   ![](assets/campaign_opt_create_control_01.png)

1. 在&#x200B;**[!UICONTROL Code]**&#x200B;选项卡中，输入要应用所需阈值的脚本，如下所示：

   ![](assets/campaign_opt_create_control_02.png)

   如果投放目标超过100个联系人，此脚本将触发警告：

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. 将此规则链接到营销活动分类，并在相关的短信投放中引用分类。

   ![](assets/campaign_opt_create_control_03.png)

1. 在投放分析期间，将应用规则并创建警告（如果适用）。

   ![](assets/campaign_opt_create_control_04.png)

   但是，投放仍可以进行发送。

   如果提高警报级别，将阻止投放开始。

   ![](assets/campaign_opt_create_control_05.png)

   分析结束时，**[!UICONTROL Confirm delivery]**&#x200B;按钮将不可用。

   ![](assets/campaign_opt_create_control_06.png)
