---
product: campaign
title: 发送、监控和跟踪短信
description: 了解如何在Campaign中发送、监控和跟踪短信
badge-v8: label="也适用于v8" type="Positive" tooltip="也适用于Campaign v8"
feature: SMS
role: User
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 3%

---

# 发送、监控和跟踪短信投放{#sms-properties}

## 发送短信消息 {#sending-sms-messages}

要批准您的消息并将其发送给正在创建的投放的收件人，请单击 **[!UICONTROL Send]**.

验证和发送投放时的详细流程将在以下部分中介绍：

* [验证投放](steps-validating-the-delivery.md)
* [发送投放](steps-sending-the-delivery.md)

## 高级参数 {#advanced-parameters}

此 **[!UICONTROL Properties]** 按钮提供了对高级投放参数的访问权限。 专用于短信投放的参数位于 **[!UICONTROL SMS parameters]** 的部分 **[!UICONTROL Delivery]** 选项卡。

可以使用以下选项：

* **发件人地址**：可让您使用限制为11个字符的字母数字字符串将投放发件人的名称个性化。 字段不能仅由数字组成。 您可以定义一个要显示的条件，例如，根据收件人的区号显示不同的名称：

  ```
  <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
  ```

  >[!IMPORTANT]
  >
  >查看您所在国家/地区有关编辑发件人姓名的法律。 您还应与操作员确认他们是否提供此功能。

* **传输模式**：通过短信传输消息。
* **优先级**：分配给消息的重要性级别。 **[!UICONTROL Normal]** 默认情况下，优先级处于选中状态。 询问您的服务提供商发送短信的费用 **[!UICONTROL High]** 优先级。
* **应用程序类型**：选择要分配给短信投放的应用程序。 此 **[!UICONTROL Direct Marketing]** 默认情况下选中该选项，并且是最常用的选项。

**NetSize连接器特定的参数**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **为单个消息使用多个短信**：利用此功能，您可以通过多条短信消息发送长度超过160个字符的消息。

**SMPP连接器特定的参数**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **每条消息的最大短信数**：利用此选项可设置用于发送消息的短信数量。 如果数字设置为0，则可以使用短信传递消息。 例如，如果短信数量设置为1或2，而消息超过此阈值，则不会发送该消息。

## 监控和跟踪短信 {#monitoring-and-tracking-sms-deliveries}

发送消息后，您可以监控和跟踪投放。 有关更多信息，请参阅一下章节。

* [监测投放](about-delivery-monitoring.md)
* [了解投放失败](understanding-delivery-failures.md)
* [关于邮件跟踪](about-message-tracking.md)

## 处理入站消息 {#processing-inbound-messages}

此 **nlserver sms** 模块定期查询短信路由器。 这允许Adobe Campaign跟踪投放的进度，并处理状态报告和收件人退订请求。

* **状态报表**：查看投放日志以检查消息的状态。

  >[!NOTE]
  >
  >发送的每个SMS都链接到其主键的外部帐户。 这样：
  >
  > * 来自已删除的外部SMS帐户的状态报表无法正确处理。
  > * 短信帐户只能链接到单个外部帐户，以确保状态报表被归因于正确的帐户

* **退订**：希望停止接收短信投放的收件人可以返回包含单词STOP的消息。 如果提供商根据合同条款允许，贵机构可通过以下方式检索报文 **入站SMS** 工作流活动，然后创建查询以启用 **不再联系此收件人** 相关收件人的选项。

  请参阅 [工作流](../../workflow/using/architecture.md) 指南。

## InSMS模式 {#insms-schema}

InSMS模式包含与传入的短信相关的信息。 这些字段的描述可通过desc属性获得。

* **message**：收到的短信的内容。
* **来源**：消息原点的手机号码。
* **providerId**：SMSC（消息中心）返回消息的标识符。
* **已创建**：将传入消息插入Adobe Campaign的日期。
* **extAccount**：Adobe Campaign外部帐户。

  >[!IMPORTANT]
  >
  >以下字段特定于NetSize。
  >
  >如果使用的运算符不是NetSize，则这些字段被视为空。

* **别名**：传入消息的别名。
* **分隔符**：消息别名和正文之间的分隔符。
* **messagedate**：操作员给定的消息日期。
* **receivalDate**：SMSC（消息中心）收到来自操作员的消息日期。
* **deliveryDate**：由SMSC（消息中心）发送的日期消息。
* **largeAccount**：链接到传入短信的客户帐户代码。
* **countryCode**：运算符国家/地区代码。
* **operatorcode**：运营商网络代码。
* **linkedSmsId**：链接到传出短信的Adobe Campaign标识符(broadlogId)，其中该SMS是响应。

## 管理自动回复（美国法规） {#managing-automatic-replies--american-regulation-}

当订阅者回复通过Adobe Campaign发送给他们的短信消息，并且他们使用STOP、HELP或YES等关键字时，在美国市场中，必须配置自动返回的消息。

例如，如果收件人发送关键字STOP ，他们会自动收到一条确认消息，声明他们已取消订阅。

此类消息的发件人名称是通常用于发送投放的简短代码。

>[!IMPORTANT]
>
>以下详细过程仅对SMPP连接器有效，扩展通用SMPP连接器除外。 有关详细信息，请参见 [创建SMPP外部帐户](sms-set-up.md#creating-an-smpp-external-account) 部分。
>
>它构成了美国运营商在美国开展营销活动的认证流程的一部分。 对订户包含关键字的短信消息的这些回复必须在收到订户的消息后立即发送回订户。

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

1. 对于 **name** 的属性 **`<shortcode>`** 标签，指定将出现在邮件发件人名称位置的短代码。

   在每个 **`<reply>`** 标签，输入 **关键词** 具有关键字的属性以及 **文本** 属性中显示的消息，您要为该关键字发送该消息。

   >[!NOTE]
   >
   >每个关键字都必须用大写字母书写。

   如果要为多个关键字发送相同的消息，请复制相应的行。

   例如：

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. 完成后，以名称保存此文件 **smsAutoReply.xml**.

   请注意，在Linux中，文件名称区分大小写。

1. 将此文件复制到 **会议** Adobe Campaign目录，与Web服务器位于同一位置。

>[!IMPORTANT]
>
>这种自动消息不会留下历史。 因此，它们不会显示在投放仪表板中。 [了解详情](delivery-dashboard.md)。
>
>商业压力规则不考虑这些报文。 [了解详情](../../campaign-opt/using/pressure-rules.md)。
