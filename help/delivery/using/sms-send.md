---
solution: Campaign Classic
product: campaign
title: 发送、监视和跟踪短信
description: 了解如何在活动中发送、监视和跟踪SMS
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 6a856c95f21b52c66a9b7359133227394fae05a5
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 2%

---


# 发送、监视和跟踪SMS投放{#sms-properties}

## 发送SMS消息{#sending-sms-messages}

要批准您的邮件并将其发送到所创建投放的收件人，请单击&#x200B;**[!UICONTROL Send]**。

验证和发送投放时的详细过程将在以下各节中介绍：

* [验证投放](../../delivery/using/steps-validating-the-delivery.md)
* [发送投放](../../delivery/using/steps-sending-the-delivery.md)

## 高级参数 {#advanced-parameters}

**[!UICONTROL Properties]**&#x200B;按钮允许访问高级投放参数。 特定于SMS投放的参数位于&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡的&#x200B;**[!UICONTROL SMS parameters]**&#x200B;部分。

可以使用以下选项：

* **发件人地址**:允许您使用限制为11个字符的字母数字字符串个性化投放发送者的名称。该领域不能只由数字组成。 您可以定义一个条件来显示，例如，根据收件人的区域代码显示不同的名称：

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >请查阅您所在国家/地区有关编辑发件人姓名的法律。 您还应询问操作员是否优惠了此功能。

* **传输模式**:短信发送
* **优先级**:为消息分配的重要级别。**[!UICONTROL Normal]** 默认情况下，优先级处于选中状态。询问您的服务提供商关于以&#x200B;**[!UICONTROL High]**&#x200B;优先级发送的SMS的成本。
* **应用程序类型**:选择要分配给您的SMS投放的应用程序。默认情况下，**[!UICONTROL Direct Marketing]**&#x200B;选项处于选中状态，是最常用的选项。

**特定于NetSize连接器的参数**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **对单条消息使用多条短信**:这样，您就可以通过多个SMS消息发送一条长度超过160个字符的消息。

**特定于SMPP连接器的参数**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **每条消息的最大短信数**:此选项允许您设置用于发送消息的SMS数。如果数字设置为0，则可以使用SMS来传送消息。 如果SMS的数量设置为1或2（例如），并且消息超过此阈值，则不会发送该消息。

## 监视和跟踪SMS {#monitoring-and-tracking-sms-deliveries}

发送消息后，您可以监视和跟踪投放。 有关更多信息，请参阅一下章节。

* [监视投放](../../delivery/using/about-delivery-monitoring.md)
* [了解投放故障](../../delivery/using/understanding-delivery-failures.md)
* [关于邮件跟踪](../../delivery/using/about-message-tracking.md)

## 处理入站消息{#processing-inbound-messages}

**nlserver sms**&#x200B;模块定期查询SMS路由器。 这使Adobe Campaign能够跟踪投放进度并处理状态报告和收件人退订请求。

* **状态报告**:视图投放日志，以检查消息的状态。

   >[!NOTE]
   >
   >发送的每条短信都链接到一个外部帐户的主键。 这样：
   >
   > * 未正确处理已删除外部SMS帐户的状态报告。
   > * SMS帐户只能链接到单个外部帐户，以确保状态报告归于正确的帐户


* **退订**:希望停止接收SMS投放的收件人可以返回包含STOP字样的消息。如果您的提供商根据合同条款允许该收件人，您可以通过&#x200B;**入站SMS**&#x200B;工作流活动检索消息，然后创建查询以为相关收件人启用&#x200B;**不再与此**&#x200B;选项。

   请参阅[工作流](../../workflow/using/architecture.md)指南。

## InSMS模式{#insms-schema}

InSMS模式包含与传入SMS相关的信息。 可通过desc属性描述这些字段。

* **消息**:收到的短信内容。
* **来源**:消息来源的移动号码。
* **providerId**:SMSC（消息中心）返回的消息的标识符。
* **created**:将传入消息插入Adobe Campaign。
* **extAccount**:Adobe Campaign外部帐户。

   >[!IMPORTANT]
   >
   >以下字段特定于NetSize。
   >
   >如果使用的运算符不是NetSize，则这些字段被视为空。

* **alias**:传入消息的别名。
* **分隔符**:别名和消息正文之间的分隔符。
* **messageDate**:运算符给出的消息日期。
* **receivalDate**:SMSC（消息中心）接收了来自运营商的日期消息。
* **deliveryDate**:SMSC（消息中心）发送的日期消息。
* **largeAccount**:链接到传入SMS的客户帐户代码
* **countryCode**:运营商国家代码。
* **operatorCode**:运营商网络代码。
* **linkedSmsId**:Adobe Campaign标识符(broadlogId)，链接到传出SMS，其中此SMS是响应。

## 管理自动回复（美国法规）{#managing-automatic-replies--american-regulation-}

当用户回复通过Adobe Campaign发送给他们的SMS消息时，他们使用STOP、HELP或YES等关键字，在美国市场中必须配置自动返回的消息。

例如，如果收件人发送关键字STOP，则他们会自动收到一条确认消息，说明他们已取消订阅。

此类消息的发件人姓名是用于发送投放的短代码。

>[!IMPORTANT]
>
>以下详细过程仅对SMPP连接器有效，扩展通用SMPP连接器除外。 有关详细信息，请参阅[创建SMPP外部帐户](sms-set-up.md#creating-an-smpp-external-account)部分。
>
>它是美国运营商为美国营销活动进行的认证过程的一部分。 在从用户接收到消息后，必须立即将这些对包含关键词的用户SMS消息的回复发回给用户。

1. 创建此类型的XML文件：

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. 对于&#x200B;**`<shortcode>`**&#x200B;标记的&#x200B;**name**&#x200B;属性，指定将在消息发送者名称的位置显示的短代码。

   在每个&#x200B;**`<reply>`**&#x200B;标记中，输入&#x200B;**关键字**&#x200B;属性和&#x200B;**文本**&#x200B;属性，并输入要为此关键字发送的消息。

   >[!NOTE]
   >
   >每个关键字都必须用大写字母书写。

   如果要为多个关键字发送相同的消息，请重复相应的行。

   例如：

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. 完成后，以&#x200B;**smsAutoReply.xml**&#x200B;名称保存此文件。

   请注意，在Linux中，文件名区分大小写。

1. 将此文件复制到Adobe Campaign中的&#x200B;**conf**&#x200B;目录中，与Web服务器位于同一位置。

>[!IMPORTANT]
>
>这类自动消息不会保留历史记录。 因此，它们不会出现在投放仪表板中。 [了解详情](../../delivery/using/delivery-dashboard.md)。
>
>这些信息在商业压力规则中没有得到考虑。 [了解详情](../../campaign/using/pressure-rules.md)。
