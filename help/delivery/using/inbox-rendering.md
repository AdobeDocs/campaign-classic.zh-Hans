---
title: 收件箱呈现
seo-title: 收件箱呈现
description: 收件箱呈现
seo-description: null
page-status-flag: never-activated
uuid: 2025f5e9-8a19-407c-9e0a-378ba5a76208
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 72e974b8-415a-47ab-9804-b15957787198
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 9%

---


# 收件箱呈现{#inbox-rendering}

## 关于收件箱渲染 {#about-inbox-rendering}

Before hitting the **Send** button, make sure that your message will be displayed to the recipients in an optimal way on a variety of web clients, web mails and devices.

为此，Adobe Campaign利用基 [于Litmus](https://litmus.com/email-testing) Web的电子邮件测试解决方案捕捉呈现内容并在专用报告中提供。 这样，您就可以在接收消息的不同上下文中预览发送的消息，并检查主要桌面和应用程序的兼容性。

Litmus是功能丰富的电子邮件验证和预览应用程序。 它允许电子邮件内容创建者在70多个电子邮件呈现器（如Gmail收件箱或Apple Mail客户端）中预览其邮件内容。

The mobile, messaging and webmail clients available for **Inbox rendering** in Adobe Campaign are listed on the [Litmus website](https://litmus.com/email-testing) (click **View all email clients**).

>[!NOTE]
>
>在投放中测试个性化不需要收件箱呈现。 可以使用Adobe Campaign工具(如和验证) **[!UICONTROL Preview]** 检查 [个性化](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

## 激活收件箱渲染 {#activating-inbox-rendering}

对于托管和混合客户端，Adobe技术支持和顾问会在您的实例上配置收件箱呈现。 有关详细信息，请与Adobe客户经理联系。

对于预置安装，请按照以下步骤配置收件箱渲染。

1. 通过 **[!UICONTROL Inbox rendering (IR)]** > >菜单 **[!UICONTROL Tools]** 安 **[!UICONTROL Advanced]** 装包 **[!UICONTROL Import package]** 。 有关此方面的详细信息，请参 [阅安装Campaign Classic标准包](../../installation/using/installing-campaign-standard-packages.md)。
1. 通过> >节点配置HTTP类 **[!UICONTROL Administration]** 型 **[!UICONTROL Platform]** 的外部帐户 **[!UICONTROL External Accounts]** 。 有关此内容的详细信息，请 [参阅创建外部帐户](../../platform/using/external-accounts.md#creating-an-external-account)。
1. 按如下方式设置外部帐户参数：
   * **[!UICONTROL Label]**:可交付性服务器信息
   * **[!UICONTROL Internal name]**:deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**:https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**:无
   * 勾选 **[!UICONTROL Enabled]** 选项。

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Go to the **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** node. 搜索选 **[!UICONTROL DmRendering_cuid]** 项和联系支持以获取需要复制到字段的投放报告标识符 **[!UICONTROL Value (text)]** 。
1. 编辑 **serverConf.xml** 文件以允许调用Litmus服务器。 在节中添加以 `<urlPermission>` 下行：

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. 使用以下命令重新加载配置：

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>您可能必须从控制台中注销并重新登录才能使用收件箱渲染。

## 关于Litmus令牌 {#about-litmus-tokens}

由于利特摩斯是第三方服务，它采用按使用计费的模式。 每次用户调用Litmus功能时，都会扣除积分。

在Adobe Campaign中，信用与可用呈现符（称为令牌）的数量相对应。

>[!NOTE]
>
>可用的Litmus令牌数量取决于您购买的活动许可证。 检查您的许可协议。

每次在投放中 **[!UICONTROL Inbox rendering]** 使用该功能时，生成的每个呈现都会将可用令牌减少一个。

>[!IMPORTANT]
>
>令牌帐户用于每个单独的呈现，而不是整个收件箱呈现报告，这意味着：
>
>* 每次生成收件箱呈现报告时，都会扣除每个消息客户端的一个令牌：一个用于Outlook 2000渲染的令牌，一个用于Outlook 2010渲染，一个用于Apple Mail 9渲染，依此类推。
>* 对于相同的投放，如果您再次生成收件箱渲染，则可用令牌的数量将再次减少为生成的渲染数量。

>



剩余的可用令牌数显示在“收件箱” **[!UICONTROL General summary]** 渲染 [报告中](#inbox-rendering-report)。

![](assets/s_tn_inbox_rendering_tokens.png)

通常，收件箱渲染功能用于测试新设计的电子邮件的HTML框架。 每个渲染需要最多70个令牌(取决于通常测试的环境数)。 但是，在某些情况下，您可能需要多个收件箱呈现报告才能完全测试投放。 因此，可能需要更多令牌才能完成多项检查。

## 访问收件箱呈现报告 {#accessing-the-inbox-rendering-report}

创建电子邮件投放并定义其内容及定向群体后，请执行以下步骤。

有关创建、设计和定位投放的详细信息，请参 [阅此部分](../../delivery/using/about-email-channel.md)。

1. 在投放顶栏上，单击按 **[!UICONTROL Inbox rendering]** 钮。
1. 选择 **[!UICONTROL Analyze]** 以开始捕获进程。

   ![](assets/s_tn_inbox_rendering_button.png)

   将发送验证。 在发送电子邮件后的几分钟内即可在该验证中访问呈现缩略图。 For more on sending proofs, refer to [this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

1. 发送后，验证显示在投放列表中。 多次单击它。

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. 转到验证 **的“收件箱** ”“渲染”选项卡。

   ![](assets/s_tn_inbox_rendering_tab.png)

   此时会显示收件箱呈现报告。

## 收件箱呈现报告 {#inbox-rendering-report}

此报告显示收件箱呈现的方式与收件人一样。 呈现方式可能因收件人打开电子邮件投放的方式而有所不同：或通过电子邮件应用程序。

作为 **[!UICONTROL General summary]** 列表和通过图形颜色编码表示来显示接收的、不想要的（垃圾邮件）、未接收的或待处理的接收的消息数。

![](assets/s_tn_inbox_rendering_summary.png)

将鼠标悬停在图表上可显示每种颜色的详细信息。

报告主体分为三部分： **[!UICONTROL Mobile]**、 **[!UICONTROL Messaging clients]**&#x200B;和 **[!UICONTROL Webmails]**。 向下滚动报告，可显示分组到这三个类别中的所有渲染。

![](assets/s_tn_inbox_rendering_report.png)

要获取各个报告的详细信息，请单击相应的卡。将针对所选的接收方式显示对应的渲染。

![](assets/s_tn_inbox_rendering_example.png)
