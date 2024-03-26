---
product: campaign
title: Campaign中的收件箱呈现
description: 了解如何捕获电子邮件渲染并在专用报告中提供它们
badge-v7: label="v7" type="Informative" tooltip="适用于Campaign Classicv7"
badge-v8: label="v8" type="Positive" tooltip="也适用于Campaign v8"
feature: Inbox Rendering, Monitoring, Email Rendering
role: User
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 7%

---

# 收件箱呈现{#inbox-rendering}

## 关于收件箱呈现 {#about-inbox-rendering}

在点击之前 **发送** 按钮，确保以最佳方式在各种Web客户端、Web邮件和设备上向收件人显示您的消息。

为了实现这一目标，Adobe Campaign利用了 [利特默斯](https://litmus.com/email-testing) 基于Web的电子邮件测试解决方案，用于捕获渲染并在专用报告中提供它们。 这样，您便可以在不同的接收环境中预览所发送的消息，并检查主要台式机和应用程序中的兼容性。

>[!CAUTION]
>收件箱呈现与不兼容 [定期投放](communication-channels.md#recurring-delivery).
>

Litmus是一款功能丰富的电子邮件验证和预览应用程序。 它允许电子邮件内容创建者在70多个电子邮件呈现器中预览其邮件内容，如Gmail收件箱或Apple Mail客户端。

移动、消息传递和网络邮件客户端可用于 **收件箱呈现** 在Adobe Campaign中， [Litmus网站](https://litmus.com/email-testing) (单击 **查看所有电子邮件客户端**)。

>[!NOTE]
>
>测试投放中的个性化不需要收件箱呈现。 可以使用Adobe Campaign工具检查个性化，例如 **[!UICONTROL Preview]** 和 [验证](steps-validating-the-delivery.md#sending-a-proof).

## 正在激活收件箱呈现 {#activating-inbox-rendering}

[!BADGE 内部部署和混合]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"}

对于托管和混合客户端，由Adobe技术支持和顾问在实例上配置收件箱呈现。 有关更多信息，请与您的Adobe客户经理联系。

对于内部部署，请按照以下步骤配置收件箱呈现。

1. 安装 **[!UICONTROL Inbox rendering (IR)]** 通过打包 **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** 菜单。 有关此内容的更多信息，请参阅 [安装Campaign Classic标准包](../../installation/using/installing-campaign-standard-packages.md).
1. 通过配置HTTP类型的外部帐户 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** 节点。 有关此内容的更多信息，请参阅 [创建外部帐户](../../installation/using/external-accounts.md#creating-an-external-account).
1. 按如下方式设置外部帐户参数：
   * **[!UICONTROL Label]**：可投放性服务器信息
   * **[!UICONTROL Internal name]**：deliverabilityInstance
   * **[!UICONTROL Type]**： HTTP
   * **[!UICONTROL Server]**： https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**：无
   * 勾选 **[!UICONTROL Enabled]** 选项。

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. 转到 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** 节点。 搜索 **[!UICONTROL DmRendering_cuid]** 选项并联系支持人员，以获取需要复制到 **[!UICONTROL Value (text)]** 字段。
1. 编辑 **serverConf.xml** 文件允许调用Litmus服务器。 将以下行添加到 `<urlPermission>` 部分：

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. 使用以下命令重新加载配置：

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>您可能需要从控制台注销并重新登录，才能使用收件箱呈现。

## 关于Litmus标记 {#about-litmus-tokens}

由于Litmus是第三方服务，因此它在基于每次使用信用的模型上运行。 每次用户调用Litmus功能时，积分都会被扣除。

在Adobe Campaign中，点数对应于可用渲染（称为令牌）的数量。

>[!NOTE]
>
>可用的Litmus令牌数量取决于您购买的Campaign许可证。 检查您的许可协议。

每次使用 **[!UICONTROL Inbox rendering]** 功能，生成的每个渲染都会将您的可用令牌减少一。

>[!IMPORTANT]
>
>令牌用于代表每个单独的渲染，而不是整个收件箱呈现报表，这意味着：
>
>* 每次生成收件箱呈现报告时，每个消息客户端都会减少一个令牌：一个令牌用于Outlook 2000呈现，一个用于Outlook 2010呈现，一个用于Apple Mail 9呈现，等等。
>* 对于同一投放，如果再次生成收件箱渲染，则可用令牌的数量将再次减少生成的渲染的数量。
>

剩余可用令牌的数量显示在 **[!UICONTROL General summary]** 的 [收件箱呈现报告](#inbox-rendering-report).

![](assets/s_tn_inbox_rendering_tokens.png)

通常，收件箱呈现功能用于测试新设计的电子邮件的HTML框架。 每次渲染大约需要70个令牌（具体取决于通常测试的环境数量）。 但是，在某些情况下，您可能需要多个收件箱呈现报告才能完全测试您的投放。 因此，可能需要更多令牌才能完成多项检查。

## 访问收件箱呈现报告 {#accessing-the-inbox-rendering-report}

创建电子邮件投放并定义其内容及定向群体后，请执行以下步骤。

有关创建、设计和定位投放的更多信息，请参阅 [本节](about-email-channel.md).

1. 在投放的顶部栏中，单击 **[!UICONTROL Inbox rendering]** 按钮。
1. 选择 **[!UICONTROL Analyze]** 以启动捕获进程。

   ![](assets/s_tn_inbox_rendering_button.png)

   已发送校样。 发送电子邮件后几分钟内，即可在该验证中访问渲染缩略图。 有关发送校样的更多信息，请参阅 [本节](steps-validating-the-delivery.md#sending-a-proof).

1. 发送后，验证会显示在投放列表中。 双击它。

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. 转到 **收件箱呈现** 选项卡中的验证。

   ![](assets/s_tn_inbox_rendering_tab.png)

   此时将显示收件箱呈现报告。

## 收件箱呈现报告 {#inbox-rendering-report}

此报告按照收件人的外观显示收件箱呈现。 根据收件人打开电子邮件投放的方式，渲染可能会有所不同：在浏览器中、移动设备上或通过电子邮件应用程序。

此 **[!UICONTROL General summary]** 通过图形颜色编码表示法将已接收、无需（垃圾邮件）、未接收或待接收的消息数显示为列表形式。

![](assets/s_tn_inbox_rendering_summary.png)

将鼠标悬停在图表上以显示每种颜色的详细信息。

报告正文分为三部分： **[!UICONTROL Mobile]**， **[!UICONTROL Messaging clients]**、和 **[!UICONTROL Webmails]**. 向下滚动报告，可显示分组到这三个类别中的所有渲染。

![](assets/s_tn_inbox_rendering_report.png)

要获取各个报告的详细信息，请单击相应的卡。将针对所选的接收方式显示对应的渲染。

![](assets/s_tn_inbox_rendering_example.png)
