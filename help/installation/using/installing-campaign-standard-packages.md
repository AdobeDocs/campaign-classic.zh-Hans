---
product: campaign
title: 安装 Campaign Classic 内置软件包
description: 了解如何安装Campaign内置软件包
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: 6c23dadb5b6523e17e242de43a908ca86ed7cc23
workflow-type: tm+mt
source-wordcount: '1188'
ht-degree: 6%

---

# 安装 Campaign Classic 内置软件包{#installing-campaign-standard-packages}

![](../../assets/v7-only.svg)

## 关于内置包 {#campaign-standard-packages}

内置软件包包含一组功能，这些功能可以根据您的需要并根据您的合同进行安装。 Campaign内置资源包的完整列表如下所示。

>[!CAUTION]
>
>您只能安装与许可协议中所述选项对应的包。
>
>安装新包可能会影响您的所有平台：在最终部署之前，必须对它进行测试和验证。
>
>安装包后，将无法卸载该包。
>
>作为托管客户或混合客户，请联系Adobe以部署新的内置资源包。

要安装内置包，请执行以下操作：

1. 从访问资源包导入向导 **[!UICONTROL Tools > Advanced > Import package]** 在Adobe Campaign客户端控制台中。
1. 选择 **[!UICONTROL Install a standard package]**。
1. 在包列表中，检查要安装的包。
   >[!NOTE]
   >
   >当包灰显时，这表示该包已安装或与您的实例不兼容。 下表详细介绍了兼容性。
1. 单击 **[!UICONTROL Next]**，则 **[!UICONTROL Start]** 以启动包安装。

   安装包后，进度栏会显示 **100%** 并且您可以在安装日志中看到以下消息： **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** 安装窗口。

现在已安装包。

### 现成包列表 {#list-of-standard-packages}

下表列出了所有Campaign内置资源包。

<table> 
 <thead> 
  <tr> 
   <th> 包 </th> 
   <th> 说明 </th> 
   <th> 实例类型 </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 投放<br /> </td> 
   <td> 监控投放以及发送消息时遇到的最终问题。 <a href="../../delivery/using/about-delivery-monitoring.md">了解详情</a><br /> </td> 
   <td> 所有</td> 
  </tr> 
  <tr> 
   <td> 营销活动（营销活动）<br /> </td> 
   <td> 定义、优化、执行和分析通信和营销活动。 <a href="../../campaign/using/designing-marketing-campaigns.md">了解更多</a><br /> </td> 
   <td> 营销</td>
  </tr> 
  <tr> 
   <td> 营销资源(MRM)<br /> </td> 
   <td> 通过提供任务、预算和营销资源的管理和跟踪，以协作模式控制营销操作。 <a href="../../mrm/using/about-marketing-resource-management.md">了解更多</a> <br /> </td> 
   <td> 营销</td> 
  </tr> 
  <tr> 
   <td> 优惠引擎（交互）<br /> </td> 
   <td> 在与给定联系人（客户或目标）的交互过程中，通过使他们成为单个或多个自适应选件进行实时响应。  可选。<a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用执行实例控制优惠引擎。 可选。<br /> </td> 
   <td> 要在选件引擎的控制实例上安装的包（交互）。 <a href="../../interaction/using/distributed-architectures.md#packages-configuration">了解更多</a> </td> 
   <td> 营销<br /> </td>  
  </tr> 
  <tr> 
   <td> 用于执行实例的选件引擎。 可选。<br /> </td> 
   <td> 要在选件引擎的执行实例上安装的包（交互）。 <a href="../../interaction/using/distributed-architectures.md">了解更多</a> </td> 
   <td> Mid，执行 <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> 社交网络（社交营销） <br /> </td> 
   <td> 将Adobe Campaign与Twitter和Facebook同步。 <a href="../../social/using/about-social-marketing.md">了解更多</a> <br /> </td> 
   <td> 所有</td> 
  </tr> 
  <tr> 
   <td> 事务型消息控制（消息中心 — 控制）<br /> </td> 
   <td> 管理从信息系统触发的事件生成的触发消息。 可选。<a href="../../message-center/using/about-transactional-messaging.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 事务型消息执行（消息中心 — 执行） <br /> </td> 
   <td> 确保更高的可用性和更好的负载管理。 可选。<a href="../../message-center/using/about-transactional-messaging.md">了解更多</a><br /> </td> 
   <td> 执行<br /> </td>
  </tr> 
  <tr> 
   <td> LINE 渠道<br /> </td> 
   <td> 使用带有Adobe Campaign的LINE渠道发送投放。 可选。事务型消息（消息中心包）是必选项。 <a href="../../delivery/using/line-channel.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 直邮渠道<br /> </td> 
   <td> 通过Adobe Campaign使用直邮渠道发送投放。 可选。<a href="../../delivery/using/about-direct-mail-channel.md">了解更多</a><br /> </td> 
   <td> 所有<br /> </td>
  </tr> 
  <tr> 
   <td> 移动渠道（短信） <br /> </td> 
   <td> 通过Adobe Campaign使用移动/短信渠道发送投放。 可选。<a href="../../delivery/using/sms-channel.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
   <tr> 
   <td> 电话渠道<br /> </td> 
   <td> 使用带有Adobe Campaign的电话渠道发送投放。 用于呼叫中心。 可选。<a href="../../delivery/using/communication-channels.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 移动应用程序渠道<br /> </td> 
   <td> 使用Adobe Campaign平台通过应用程序向iOS和Android终端发送个性化通知。 可选。<a href="../../delivery/using/about-mobile-app-channel.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 内容管理器<br /> </td> 
   <td> 创建定期新闻稿或网站，然后验证并发布您的消息。 <a href="../../delivery/using/about-content-management.md">了解更多</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> 在线调查（调查管理器）<br /> </td> 
   <td> 创建并管理在线表单以添加或修改用户档案信息、订阅、退订或竞争条目表单。 可选。<a href="../../surveys/using/about-surveys.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 营销分析<br /> </td> 
   <td> 使您能够分析和测量数据、计算统计数据、简化和优化报表的创建和计算。 此外，您还可以创建报表并构建目标群体。 可选。<a href="../../reporting/using/about-cubes.md">了解更多</a><br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 响应管理器<br /> </td> 
   <td> 衡量营销活动的成功和盈利能力，或为所有沟通渠道提供建议。  可选。<a href="../../response/using/about-response-manager.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 外部数据访问（联合数据访问）<br /> </td> 
   <td> 提供联合数据访问(FDA)选项，以便处理存储在一个或多个外部数据库中的信息，以便您能够访问外部数据，而无需更改Adobe Campaign数据的结构。  可选。<a href="../../workflow/using/accessing-an-external-database--fda-.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 活动优化<br /> </td> 
   <td> 控制、过滤和监控投放的发送，以便按照公司通信策略，最好地满足客户的需求和期望。 可选。<a href="../../campaign-opt/using/about-campaign-typologies.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 投放能力监控（电子邮件投放能力）<br /> </td> 
   <td> 衡量活动是否成功到达收件人的收件箱，而不会出现弹回或标记为垃圾邮件。 可选。<a href="../../delivery/using/about-deliverability.md">了解更多</a> <br /> </td> 
   <td> 所有 </td> 
  </tr> 
  <tr> 
   <td> 优惠券管理<br /> </td> 
   <td> 创建一组优惠券以添加到即将推出的营销选件。 可选。<a href="../../delivery/using/personalized-coupons.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件箱呈现(IR)<br /> </td> 
   <td> 允许您预览在可能收到消息的不同上下文中发送的消息，并检查主要桌面和应用程序的兼容性。 可选。<a href="../../delivery/using/inbox-rendering.md">了解更多</a><br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 中央/地方营销（分布式营销）<br /> </td> 
   <td> 在中央实体（总部、营销部门等）之间实施合作活动 和地方实体（销售点、地区机构等）。 可选。<a href="../../distributed/using/about-distributed-marketing.md">了解更多</a><br /> </td> 
   <td> 营销 </td> 
  </tr> 
  <tr> 
   <td> CRM 连接器<br /> </td> 
   <td> 提供各种CRM连接器，用于将Adobe Campaign平台关联到第三方系统。  <a href="../../platform/using/crm-connectors.md">了解更多</a> <br /> </td> 
   <td> 营销</td> 
  </tr> 
  <tr> 
   <td> Web Analytics连接器<br /> </td> 
   <td> 允许Adobe Campaign和Adobe Analytics通过Web Analytics连接器包进行交互。 与事务型消息（消息中心包）不兼容。 <a href="../../platform/using/adobe-analytics-connector.md">了解更多</a><br /> </td> 
   <td> 营销 </td> 
  </tr> 
  <tr> 
   <td> AEM集成<br /> </td> 
   <td> 允许您直接在Adobe Experience Manager中管理电子邮件投放的内容和表单，以便从AEM内容编辑功能和Adobe Campaign的投放能力中受益。 <a href="../../integrations/using/about-adobe-experience-manager.md">了解更多</a> <br /> </td> 
   <td> 营销</td> 
  </tr> 
  <tr> 
   <td> Adobe Experience Cloud共享受众集成<br /> </td> 
   <td> 允许您使用Adobe Experience Cloud解决方案和核心服务交换和共享受众/区段。 需要IMS <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 与Adobe Experience Cloud集成<br /> </td> 
   <td> 允许您将不同Adobe Experience Cloud解决方案中的受众/区段导入和导出到Adobe Campaign。 可选。<a href="../../integrations/using/configuring-ims.md#installing-the-package">了解更多</a> </td> 
   <td> 营销</td> 
  </tr> 
  <tr> 
   <td> 隐私数据保护规定<br /> </td> 
   <td> 包含其他功能，可帮助您在Campaign Classic中遵守隐私规定。 <a href="https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html">了解更多</a> <br /> </td> 
   <td> 所有</td> 
  </tr> 
  <tr> 
   <td> 传输到中间源 <br /> </td> 
   <td> 详细介绍中间源服务器的安装和配置，以及使第三方能够在中间源模式下发送消息的实例的部署。 可选。<a href="../../installation/using/mid-sourcing-server.md">了解更多</a> <br /> </td> 
   <td> 营销 </td> 
  </tr> 
  <tr> 
   <td> 中间源平台<br /> </td> 
   <td> 此配置是托管(ASP)配置与内部化之间的最佳中间解决方案。 面向外的执行组件在托管在Adobe Campaign的“中间源”服务器上执行。 可选。<a href="../../installation/using/mid-sourcing-server.md">了解更多</a> <br /> </td> 
   <td> 中间源 </td> 
  </tr> 
  <tr> 
   <td> AMP支持<br /> </td> 
   <td> 允许您使用新的交互式AMP进行电子邮件格式，并发送动态电子邮件。 可选。<a href="../../delivery/using/defining-interactive-content.md">了解更多</a> <br /> </td> 
   <td> 所有 </td> 
  </tr> 
  <tr> 
   <td> ACS 连接器<br /> </td> 
   <td> 桥梁Adobe Campaign v7和Adobe Campaign Standard。 它是Campaign v7中的一项集成功能，可自动将数据复制到Campaign Standard，从而将两个应用程序中的最佳功能结合起来。 可选。<a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">了解更多</a> <br /> </td> 
   <td> 营销 </td> 
  </tr> 
 </tbody> 
</table>

### 消息中心包 {#message-center-package}

您必须安装投放渠道（电子邮件、移动设备渠道、移动设备应用程序渠道等） 安装事务性消息（消息中心包）之前。 如果您已启动仅限电子邮件的消息中心项目，并且随后需要添加新渠道，则必须执行以下步骤：

1. 安装新渠道，例如 **移动渠道**，使用资源包导入向导( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**)。
1. 导入文件( **[!UICONTROL Tools > Advanced > Import package > File]**)，然后选择：

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. 在 **[!UICONTROL XML data content to import]**，则仅保留与相关渠道对应的消息中心投放模板。 例如，如果您已将 **移动渠道**，则仅保留 **实体** 对应于 **[!UICONTROL Mobile transactional message]** (smsTriggerMessage)模板。 如果您已将 **移动设备应用程序渠道**，则仅保留 **iOS事务型消息** 模板(iosTriggerMessage)和 **Android事务型消息** (androidTriggerMessage)。

   ![](assets/messagecenter_install_channel.png)

>[!CAUTION]
>
>如果在LINE之前安装了消息中心包，则LINE的消息中心投放模板将不可用
