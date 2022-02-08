---
product: campaign
title: 发送、监控和跟踪短信
description: 了解如何在Campaign中发送、监控和跟踪短信
feature: SMS
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 3%

---

# 发送、监控和跟踪短信投放{#sms-properties}

![](../../assets/common.svg)

## 发送短信消息 {#sending-sms-messages}

要批准消息并将其发送给所创建投放的收件人，请单击 **[!UICONTROL Send]**.

有关验证和发送投放的详细过程，请参阅以下章节：

* [验证投放](steps-validating-the-delivery.md)
* [发送投放](steps-sending-the-delivery.md)

## 高级参数 {#advanced-parameters}

的 **[!UICONTROL Properties]** 按钮，可访问高级提交参数。 特定于短信投放的参数位于 **[!UICONTROL SMS parameters]** 部分 **[!UICONTROL Delivery]** 选项卡。

可以使用以下选项：

* **发件人地址**:允许您使用限制为11个字符的字母数字字符字符串来个性化投放发件人的名称。 字段不能只由数字组成。 您可以定义一个条件来显示不同的名称，例如，根据收件人的区号显示不同的名称：

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >查看您所在国家/地区有关编辑发件人姓名的法律。 您还应咨询操作员是否提供此功能。

* **传输模式**:短信报文传输
* **优先级**:消息的重要级别。 **[!UICONTROL Normal]** 默认情况下，优先级处于选中状态。 向您的服务提供商咨询随 **[!UICONTROL High]** 优先级。
* **应用程序类型**:选择要分配给短信投放的应用程序。 的 **[!UICONTROL Direct Marketing]** 选项，它是最常用的选项。

**特定于NetSize连接器的参数**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **对单个消息使用多条短信**:这允许您通过多条短信消息，发送长度超过160个字符的消息。

**特定于SMPP连接器的参数**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **每条消息的最大短信数**:利用此选项，可设置用于发送消息的短信数量。 如果数字设置为0，则可以使用短信来传递消息。 例如，如果短信的数量设置为1或2，并且消息超过此阈值，则不会发送该消息。

## 监控和跟踪短信 {#monitoring-and-tracking-sms-deliveries}

发送消息后，您可以监控和跟踪投放内容。 有关更多信息，请参阅一下章节。

* [监测投放](about-delivery-monitoring.md)
* [了解投放失败](understanding-delivery-failures.md)
* [关于邮件跟踪](about-message-tracking.md)

## 处理入站消息 {#processing-inbound-messages}

的 **nlserver sms** 模块定期查询短信路由器。 这允许Adobe Campaign跟踪投放进度并处理状态报告和收件人退订请求。

* **状态报表**:查看投放日志以检查消息的状态。

   >[!NOTE]
   >
   >发送的每条短信都会链接到外部帐户及其主密钥。 这样：
   >
   > * 未正确处理来自已删除外部短信帐户的状态报告。
   > * 短信帐户只能链接到单个外部帐户，以确保状态报表归因到正确的帐户


* **退订**:希望停止接收短信投放的收件人可返回包含STOP字样的消息。 如果您的提供商根据合同条款允许它，则可以通过 **入站短信** 工作流活动，然后创建查询以启用 **不再联系此收件人** 选项。

   请参阅 [工作流](../../workflow/using/architecture.md) 的双曲余切值。

## InSMS模式 {#insms-schema}

InSMS架构包含与传入短信相关的信息。 可通过desc属性描述这些字段。

* **消息**:收到的短信内容。
* **来源**:消息源处的移动号码。
* **providerId**:SMSC（消息中心）返回的消息的标识符。
* **已创建**:日期传入消息已插入Adobe Campaign。
* **extAccount**:Adobe Campaign外部帐户。

   >[!IMPORTANT]
   >
   >以下字段专用于NetSize。
   >
   >如果使用的运算符不是NetSize，则这些字段会被视为空。

* **别名**:传入消息的别名。
* **分隔符**:别名和消息正文之间的分隔符。
* **messageDate**:操作员提供的消息日期。
* **receivalDate**:SMSC（消息中心）接收到操作员的日期消息。
* **deliveryDate**:由SMSC（消息中心）发送的日期消息。
* **largeAccount**:链接到传入短信的客户帐户代码
* **countryCode**:操作员国家/地区代码。
* **operatorCode**:操作员网络代码。
* **linkedSmsId**:Adobe Campaign标识符(broadlogId)，链接到传出短信，其中此短信是响应。

## 管理自动回复（美国法规） {#managing-automatic-replies--american-regulation-}

当订阅者回复通过Adobe Campaign发送给他们的短信消息，并且使用STOP、HELP或YES等关键字时，美国市场上有必要配置自动返回的消息。

例如，如果收件人发送关键词STOP，则他们会自动收到确认消息，声明他们已取消订阅。

此类消息的发件人名称是用于发送投放的简短代码。

>[!IMPORTANT]
>
>以下详细过程仅对SMPP连接器有效，扩展的通用SMPP连接器除外。 有关更多信息，请参阅 [创建SMPP外部帐户](sms-set-up.md#creating-an-smpp-external-account) 中。
>
>它构成了美国运营商在美国开展营销活动的认证过程的一部分。 在收到包含关键词的订阅者短信消息后，必须立即将这些消息回复回订阅者。

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

1. 对于 **name** 属性 **`<shortcode>`** 标记，指定将在消息发送者名称的位置显示的短代码。

   在 **`<reply>`** 标记，输入 **关键词** 属性 **文本** 属性。

   >[!NOTE]
   >
   >每个关键词必须用大写字母写。

   如果要为多个关键词发送相同的消息，请复制相应的行。

   例如：

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. 完成后，请使用名称保存此文件 **smsAutoReply.xml**.

   请注意，在Linux中，文件名称区分大小写。

1. 将此文件复制到 **conf** 目录中，与Web服务器位于同一位置。

>[!IMPORTANT]
>
>这类自动报文不会保留历史记录。 因此，它们不会显示在投放仪表板中。 [了解详情](delivery-dashboard.md)。
>
>商业压力规则未考虑这些报文。 [了解详情](../../campaign-opt/using/pressure-rules.md)。
