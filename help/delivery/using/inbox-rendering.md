---
solution: Campaign Classic
product: campaign
title: 收件箱呈现在活动
description: 了解如何捕获电子邮件呈现并在专用报告中提供
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 8%

---


# 收件箱呈现{#inbox-rendering}

## 关于收件箱呈现{#about-inbox-rendering}

在点击&#x200B;**发送**&#x200B;按钮之前，请确保您的消息将以最佳方式在各种Web客户端、Web邮件和设备上显示给收件人。

为此，Adobe Campaign利用[Litmus](https://litmus.com/email-testing)基于Web的电子邮件测试解决方案来捕获呈现内容并在专用报告中提供。 这使您能够在接收消息的不同上下文预览发送的消息，并检查主要桌面和应用程序的兼容性。

Litmus是一个功能丰富的电子邮件验证和预览应用程序。 它允许电子邮件内容创建者在70多个电子邮件呈示器（如Gmail收件箱或Apple Mail客户端）中预览其邮件内容。

[Litmus网站](https://litmus.com/email-testing)上列出了可用于Adobe Campaign中&#x200B;**收件箱呈现**&#x200B;的移动设备、消息和Web邮件客户端(单击&#x200B;**视图所有电子邮件客户端**)。

>[!NOTE]
>
>在测试投放中的个性化时，不必呈现收件箱。 可以使用Adobe Campaign工具(如&#x200B;**[!UICONTROL Preview]**&#x200B;和[验证](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof))来检查个性化。

## 激活收件箱呈现{#activating-inbox-rendering}

对于托管和混合客户端，Adobe技术支持和顾问会在您的实例上配置收件箱呈现。 有关详细信息，请与Adobe客户经理联系。

对于内部部署安装，请按照以下步骤配置收件箱渲染。

1. 通过&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**&#x200B;菜单安装&#x200B;**[!UICONTROL Inbox rendering (IR)]**&#x200B;包。 有关详细信息，请参阅[安装Campaign Classic标准包](../../installation/using/installing-campaign-standard-packages.md)。
1. 通过&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**&#x200B;节点配置HTTP类型的外部帐户。 有关详细信息，请参阅[创建外部帐户](../../installation/using/external-accounts.md#creating-an-external-account)。
1. 按如下方式设置外部帐户参数：
   * **[!UICONTROL Label]**:可交付性服务器信息
   * **[!UICONTROL Internal name]**:deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**:https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**:无
   * 勾选 **[!UICONTROL Enabled]** 选项。

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. 转到&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;节点。 搜索&#x200B;**[!UICONTROL DmRendering_cuid]**&#x200B;选项并与支持部门联系，以获取需要复制到&#x200B;**[!UICONTROL Value (text)]**&#x200B;字段的投放报告标识符。
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
>您可能需要从控制台注销并重新登录才能使用收件箱渲染。

## 关于Litmus令牌{#about-litmus-tokens}

由于利特谟是第三方服务，它采用按使用计费的模式。 每次用户调用Litmus功能时，都会扣除信用。

在Adobe Campaign中，信用对应于可用呈现次数（称为令牌）。

>[!NOTE]
>
>可用的Litmus令牌数量取决于您购买的活动许可。 检查您的许可协议。

每次在投放中使用&#x200B;**[!UICONTROL Inbox rendering]**&#x200B;功能时，生成的每个呈现都会将可用令牌减少一个。

>[!IMPORTANT]
>
>令牌帐户用于每个呈现，而非整个收件箱呈现报表，这意味着：
>
>* 每次生成收件箱呈现报告时，都会扣除每个消息客户端的一个令牌：一个用于Outlook 2000渲染的令牌，一个用于Outlook 2010渲染，一个用于Apple Mail 9渲染，依此类推。
>* 对于同一投放，如果您再次生成收件箱渲染，则可用令牌的数量会再次减少生成的渲染。
>



剩余可用令牌的数量显示在[收件箱呈现报告](#inbox-rendering-report)的&#x200B;**[!UICONTROL General summary]**&#x200B;中。

![](assets/s_tn_inbox_rendering_tokens.png)

通常，收件箱渲染功能用于测试新设计的电子邮件的HTML框架。 每个渲染需要最多70个令牌(具体取决于通常测试的环境数量)。 但是，在某些情况下，您可能需要多个收件箱呈现报告才能完全测试投放。 因此，可能需要更多令牌才能完成多项检查。

## 访问收件箱呈现报告{#accessing-the-inbox-rendering-report}

创建电子邮件投放并定义其内容及定向群体后，请执行以下步骤。

有关创建、设计和定位投放的详细信息，请参阅[本节](../../delivery/using/about-email-channel.md)。

1. 在投放顶栏上，单击&#x200B;**[!UICONTROL Inbox rendering]**&#x200B;按钮。
1. 选择&#x200B;**[!UICONTROL Analyze]**&#x200B;以开始捕获进程。

   ![](assets/s_tn_inbox_rendering_button.png)

   将发送验证。 在发送电子邮件后的几分钟内即可在该验证中访问呈现缩略图。 有关发送验证的详细信息，请参阅[本节](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)。

1. 发送后，验证将显示在投放列表中。 多次单击它。

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. 转到验证的&#x200B;**收件箱渲染**&#x200B;选项卡。

   ![](assets/s_tn_inbox_rendering_tab.png)

   此时将显示收件箱呈现报告。

## 收件箱呈现报告{#inbox-rendering-report}

此报表显示收件箱呈现的收件人。 呈现方式可能因收件人打开电子邮件投放的方式而异：或通过电子邮件应用程序。

**[!UICONTROL General summary]**&#x200B;以列表和图形颜色编码表示形式显示接收、不想要（垃圾邮件）、未接收或待处理接收的消息数。

![](assets/s_tn_inbox_rendering_summary.png)

将鼠标悬停在图表上可显示每种颜色的详细信息。

报告正文分为三部分：**[!UICONTROL Mobile]**、**[!UICONTROL Messaging clients]**&#x200B;和&#x200B;**[!UICONTROL Webmails]**。 向下滚动报告，可显示分组到这三个类别中的所有渲染。

![](assets/s_tn_inbox_rendering_report.png)

要获取各个报告的详细信息，请单击相应的卡。将针对所选的接收方式显示对应的渲染。

![](assets/s_tn_inbox_rendering_example.png)
