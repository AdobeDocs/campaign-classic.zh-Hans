---
product: campaign
title: 控制规则
description: 了解如何使用Adobe Campaign中的控制规则
role: User, Developer
feature: Typology Rules, Campaigns
hide: true
exl-id: 5a5f26f6-38da-4488-aadb-81fcb5359331
TQID: https://experienceleague.adobe.com/zeKJZ7Y-qtGpPtZ6tUPN42ISVU6Fh6wpOuhfcXDsyAA
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616a
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 368
ht-degree: 2%

---

# 控制规则{#control-rules}

## 分析和仲裁控制规则 {#analysis-and-arbitration-control-rules}

利用控制规则，您可以保证消息在投放前的有效性和质量：字符显示、短信大小、地址格式等。

通过一组现成的规则，可执行常规检查。 这些检查（在界面中以粗体显示）包括：

* **[!UICONTROL Object approval]** （电子邮件）：检查发件人对象和地址是否不包含可能导致某些邮件代理出现问题的特殊字符。
* **[!UICONTROL URL label approval]** （电子邮件）：检查每个跟踪URL是否都有标签。
* **[!UICONTROL URL approval]** （电子邮件）：检查跟踪URL（存在“&amp;”字符）。
* **[!UICONTROL Message size approval]** （移动设备）：检查SMS消息的大小。
* **[!UICONTROL Validity period check]** （电子邮件）：检查投放的有效期是否足以发送所有邮件。
* **[!UICONTROL Proof size check]** （所有渠道）：如果验证目标群体超过100个收件人，则生成错误消息。
* **[!UICONTROL Wave scheduling check]** （电子邮件）：如果投放被细分为多个阶段，则检查是否计划在有效期结束前开始最后一波投放。
* **[!UICONTROL Unsubscription link approval]** （电子邮件）：检查每个内容（HTML和文本）中是否存在至少一个退订（选择退出）URL。

## 创建控制规则 {#creating-a-control-rule}

可以创建新的控制规则以满足您的需求。 为此，请创建一个&#x200B;**[!UICONTROL Control]**&#x200B;分类规则，并在&#x200B;**[!UICONTROL Code]**&#x200B;选项卡的SQL中输入控制公式。

**示例：**

在以下示例中，我们将创建一个规则，以防止将短信选件发送给100个以上的收件人。 此规则将链接到活动类型，然后链接到相关选件可用的短信投放。

应用以下步骤：

1. 创建&#x200B;**[!UICONTROL Control]**&#x200B;分类规则。 选择&#x200B;**[!UICONTROL Warning]**&#x200B;警报级别。

   ![](assets/campaign_opt_create_control_01.png)

1. 在&#x200B;**[!UICONTROL Code]**&#x200B;选项卡中，输入脚本以应用所需的阈值，如下所示：

   ![](assets/campaign_opt_create_control_02.png)

   如果投放目标超过100个联系人，此脚本将触发警告：

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. 将此规则链接到活动分类，并在相关短信投放中引用该分类。

   ![](assets/campaign_opt_create_control_03.png)

1. 在投放分析期间，会应用规则并创建警告（如果适用）。

   ![](assets/campaign_opt_create_control_04.png)

   但是，投放仍然可以发送。

   如果提高警报级别，则会阻止开始投放。

   ![](assets/campaign_opt_create_control_05.png)

   分析结束时，**[!UICONTROL Confirm delivery]**&#x200B;按钮将不可用。

   ![](assets/campaign_opt_create_control_06.png)
