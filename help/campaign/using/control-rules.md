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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# 控制规则{#control-rules}

## 分析与仲裁控制规则 {#analysis-and-arbitration-control-rules}

通过控制规则，您可以在发送邮件之前保证邮件的有效性和质量：字符显示、SMS大小、地址格式等。

一套现成的规则允许您执行常规检查。 这些检查（在界面中以粗体显示）包括：

* **[!UICONTROL Object approval]** （电子邮件）:检查发送方对象和地址是否不包含可能导致某些邮件代理出现问题的特殊字符。
* **[!UICONTROL URL label approval]** （电子邮件）:检查每个跟踪URL是否都有标签。
* **[!UICONTROL URL approval]** （电子邮件）:检查跟踪URL（存在“&amp;”字符）。
* **[!UICONTROL Message size approval]** （移动）:检查SMS消息的大小。
* **[!UICONTROL Validity period check]** （电子邮件）:检查发送的有效期是否长到足以发送所有消息。
* **[!UICONTROL Proof size check]** （所有渠道）:如果证明目标数量超过100个接收者，则生成错误消息。
* **[!UICONTROL Wave scheduling check]** （电子邮件）:检查如果交付被分解为多个波，则最后一波交付是否预定在有效期结束之前开始。
* **[!UICONTROL Unsubscription link approval]** （电子邮件）:检查每个内容（HTML和文本）中是否存在至少一个取消订阅（退出）URL。

## 创建控件规则 {#creating-a-control-rule}

可以创建满足您需求的新控制规则。 为此，请创建一个 **[!UICONTROL Control]** 排版规则，并在选项卡的SQL中输入控制公 **[!UICONTROL Code]** 式。

**例如：**

在以下示例中，我们将创建一个规则，以防止将SMS选件发送到100多个收件人。 此规则将链接到营销活动类型学，然后链接到相关推广信息可用的SMS分发。

应用以下步骤：

1. 创建 **[!UICONTROL Control]** 排版规则。 选择警 **[!UICONTROL Warning]** 报级别。

   ![](assets/campaign_opt_create_control_01.png)

1. 在选项卡 **[!UICONTROL Code]** 中，输入要应用所需阈值的脚本，如下所示：

   ![](assets/campaign_opt_create_control_02.png)

   如果传送目标超过100个联系人，此脚本将触发警告：

   ```
   if( delivery.FCP == false && delivery.properties.toDeliver > 100 ) { logWarning("Significant number of SMS to deliver (" + delivery.properties.toDeliver + "). Please make sure the target is correct.") return false; } return true
   ```

1. 将此规则链接到营销活动类型学，并参考相关SMS交付中的类型学。

   ![](assets/campaign_opt_create_control_03.png)

1. 在交付分析过程中，将应用该规则并创建警告（如果适用）。

   ![](assets/campaign_opt_create_control_04.png)

   但是，交付仍可进行发送。

   如果您提高警报级别，这将阻止发送开始。

   ![](assets/campaign_opt_create_control_05.png)

   分析结束时，该按 **[!UICONTROL Confirm delivery]** 钮将不可用。

   ![](assets/campaign_opt_create_control_06.png)

