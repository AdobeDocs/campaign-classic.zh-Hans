---
product: campaign
title: Campaign中的收件箱呈现
description: 了解如何捕获电子邮件渲染并在专用报告中提供
audience: delivery
content-type: reference
topic-tags: deliverability-management
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 8%

---

# 收件箱呈现{#inbox-rendering}

![](../../assets/common.svg)

## 关于收件箱呈现 {#about-inbox-rendering}

在点击&#x200B;**发送**&#x200B;按钮之前，确保以最佳方式在各种Web客户端、Web邮件和设备上向收件人显示您的消息。

为实现此目的，Adobe Campaign利用[Litmus](https://litmus.com/email-testing)基于Web的电子邮件测试解决方案来捕获渲染并在专用报告中提供。 这样，您就可以预览不同上下文中可能收到的已发送消息，并检查主要桌面和应用程序的兼容性。

Litmus是一种功能丰富的电子邮件验证和预览应用程序。 它允许电子邮件内容创建者在70多个电子邮件渲染器（如Gmail收件箱或Apple Mail客户端）中预览其消息内容。

可用于Adobe Campaign中&#x200B;**收件箱呈现**&#x200B;的移动设备、消息传送和Web邮件客户端列在[Litmus网站](https://litmus.com/email-testing)（单击&#x200B;**查看所有电子邮件客户端**）上。

>[!NOTE]
>
>在投放中测试个性化无需进行收件箱呈现。 可以使用Adobe Campaign工具（如&#x200B;**[!UICONTROL Preview]**&#x200B;和[校样](steps-validating-the-delivery.md#sending-a-proof)）检查个性化。

## 激活收件箱呈现 {#activating-inbox-rendering}

对于托管和混合客户端，Adobe技术支持和顾问会在您的实例上配置收件箱呈现。 有关更多信息，请联系您的Adobe客户经理。

对于内部部署安装，请按照以下步骤配置收件箱呈现。

1. 通过&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**&#x200B;菜单安装&#x200B;**[!UICONTROL Inbox rendering (IR)]**&#x200B;包。 有关更多信息，请参阅[安装Campaign Classic标准包](../../installation/using/installing-campaign-standard-packages.md)。
1. 通过&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**&#x200B;节点配置HTTP类型的外部帐户。 有关更多信息，请参阅[创建外部帐户](../../installation/using/external-accounts.md#creating-an-external-account)。
1. 按如下方式设置外部帐户参数：
   * **[!UICONTROL Label]**:可投放性服务器信息
   * **[!UICONTROL Internal name]**:deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**:https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**:无
   * 勾选 **[!UICONTROL Enabled]** 选项。

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. 转到&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;节点。 搜索&#x200B;**[!UICONTROL DmRendering_cuid]**&#x200B;选项并联系支持人员，以获取需要复制到&#x200B;**[!UICONTROL Value (text)]**&#x200B;字段的投放报告标识符。
1. 编辑&#x200B;**serverConf.xml**&#x200B;文件，以允许调用Litmus服务器。 在`<urlPermission>`部分添加以下行：

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. 使用以下命令重新加载配置：

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>您可能需要从控制台注销并重新登录才能使用收件箱呈现功能。

## 关于Litmus令牌 {#about-litmus-tokens}

由于利特摩是第三方服务，因此它采用的是按使用计费的模式。 每次用户调用Litmus功能时，都会扣除点数。

在Adobe Campaign中，点数对应于可用渲染（称为令牌）的数量。

>[!NOTE]
>
>可用的Litmus令牌数量取决于您购买的Campaign许可证。 检查您的许可协议。

每次在投放中使用&#x200B;**[!UICONTROL Inbox rendering]**&#x200B;功能时，生成的每个渲染都会将可用令牌数量减一。

>[!IMPORTANT]
>
>令牌用于每个人的渲染，而不用于整个收件箱渲染报表，这意味着：
>
>* 每次生成收件箱呈现报告时，都会为每个消息传送客户端扣除一个令牌：一个用于Outlook 2000渲染的令牌，一个用于Outlook 2010渲染的令牌，一个用于Apple Mail 9渲染，等等。
>* 对于同一投放，如果您再次生成收件箱呈现，则可用令牌的数量会再次减少所生成渲染的数量。

>


剩余的可用令牌数显示在[收件箱呈现报表](#inbox-rendering-report)的&#x200B;**[!UICONTROL General summary]**&#x200B;中。

![](assets/s_tn_inbox_rendering_tokens.png)

通常，收件箱呈现功能用于测试新设计电子邮件的HTML框架。 每个渲染最多需要70个令牌（具体取决于通常测试的环境数量）。 但是，在某些情况下，您可能需要多个收件箱呈现报告才能完全测试您的投放。 因此，可能需要更多令牌才能完成多项检查。

## 访问收件箱呈现报告 {#accessing-the-inbox-rendering-report}

创建电子邮件投放并定义其内容及定向群体后，请执行以下步骤。

有关创建、设计和定位投放的更多信息，请参阅[此部分](about-email-channel.md)。

1. 单击投放顶部栏的&#x200B;**[!UICONTROL Inbox rendering]**&#x200B;按钮。
1. 选择&#x200B;**[!UICONTROL Analyze]**&#x200B;以启动捕获进程。

   ![](assets/s_tn_inbox_rendering_button.png)

   发送校样。 在发送电子邮件后几分钟，可以在校样中访问渲染缩略图。 有关发送校样的更多信息，请参阅[此部分](steps-validating-the-delivery.md#sending-a-proof)。

1. 发送校样后，该校样会显示在投放列表中。 双击它。

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. 转到校样的&#x200B;**Inbox Rendering**&#x200B;选项卡。

   ![](assets/s_tn_inbox_rendering_tab.png)

   将显示收件箱呈现报告。

## 收件箱呈现报告 {#inbox-rendering-report}

此报表显示收件人看到的收件箱呈现。 呈现方式可能因收件人打开电子邮件投放的方式而异：浏览器、移动设备或电子邮件应用程序中。

**[!UICONTROL General summary]**&#x200B;以列表形式和图形颜色编码表示接收的消息数、无用的（垃圾邮件）消息数、未接收的消息数或待接收的消息数。

![](assets/s_tn_inbox_rendering_summary.png)

将鼠标悬停在图表上可显示每种颜色的详细信息。

报告正文分为三部分：**[!UICONTROL Mobile]**、**[!UICONTROL Messaging clients]**&#x200B;和&#x200B;**[!UICONTROL Webmails]**。 向下滚动报告，可显示分组到这三个类别中的所有渲染。

![](assets/s_tn_inbox_rendering_report.png)

要获取各个报告的详细信息，请单击相应的卡。将针对所选的接收方式显示对应的渲染。

![](assets/s_tn_inbox_rendering_example.png)
