---
title: 安装Campaign Classic标准包
seo-title: 安装Campaign Classic标准包
description: 安装Campaign Classic标准包
seo-description: null
page-status-flag: never-activated
uuid: 1cba9487-52fc-442f-ae99-f8a2c157f25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: dd8f9adf-208c-42d9-b1a7-bfc8a690687e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: efef031d9c662daac6634ff7cc0d05d9d512443b

---


# 安装Campaign Classic标准包{#installing-campaign-standard-packages}

## 关于标准包 {#campaign-standard-packages}

包是一组功能，可根据您的需要安装。 它们允许您向实例添加更多选项。

>[!CAUTION]
>
>您只能安装与许可合同中所述选项相对应的包。
>
>安装包后，便无法卸载它。 安装新包可能会影响您的所有平台：在最终部署之前，它必须经过测试和验证。

安装标准包：

1. 从导入向导客户端控制台 **[!UICONTROL Tools > Advanced > Package import...]** 中访问包Adobe Campaign。
1. Select **[!UICONTROL Install a standard package]**.
1. 在显示的列表中，检查要安装的包。
   >[!NOTE]
   >
   >如果包灰显，则无法安装它。 这表示已安装或与实例不兼容。 例如，您无法在营销实例 **上安装中间源平** 台包。 您将在下表中找到此信息。
1. 单 **[!UICONTROL Next]**&#x200B;击，然 **[!UICONTROL Start]** 后开始包安装。

   安装包后，进度栏显示 **100%** ，并且您可以在安装日志中看到以下消息： **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** 安装窗口。

现在已安装包。

### 列表现成包 {#list-of-standard-packages}

下表列表了所有标准包及其说明、可安装的实例类型（Marketing、Mid等）和其他信息。

<table> 
 <thead> 
  <tr> 
   <th> 包 </th> 
   <th> 说明 </th> 
   <th> 实例类型 </th> 
   <th> 更多信息 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 投放<br /> </td> 
   <td> 监视发送消息时遇到的投放和最终问题。<br /> </td> 
   <td> 所有</td> 
   <td> <a href="../../delivery/using/monitoring-a-delivery.md">了解更多</a></td> 
  </tr> 
  <tr> 
   <td> 营销活动(活动)<br /> </td> 
   <td> 定义、优化、执行和分析通信和营销活动。<br /> </td> 
   <td> 营销</td> 
   <td> <a href="../../campaign/using/designing-marketing-campaigns.md">了解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 营销资源语(MRM)<br /> </td> 
   <td> 通过提供对任务、预算和营销资源的管理和跟踪，以协作模式控制营销活动。<br /> </td> 
   <td> 营销</td> 
   <td> <a href="../../campaign/using/about-marketing-resource-management.md">了解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 优惠引擎（交互）<br /> </td> 
   <td> 在与给定联系人(客户或目标)的交互过程中，通过使其成为单个或多个调整的优惠实时做出响应。 <br /> </td> 
   <td> 所有<br /> </td> 
   <td> 可选，了 <a href="../../interaction/using/interaction-and-offer-management.md">解更多</a></td> 
  </tr> 
  <tr> 
   <td> 具有执行实例的优惠发动机的控制<br /> </td> 
   <td> </td> 
   <td> 营销<br /> </td> 
   <td> 可选</td> 
  </tr> 
  <tr> 
   <td> 优惠引擎<br /> </td> 
   <td> </td> 
   <td> Mid，执行 <br /> </td> 
   <td> 可选</td> 
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> 社交网络（社交营销） <br /> </td> 
   <td> 将Adobe Campaign与Twitter和Facebook同步。<br /> </td> 
   <td> 所有</td> 
   <td> <a href="../../social/using/about-social-marketing.md">了解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 事务性消息控制（消息中心——控制）<br /> </td> 
   <td> 管理从信息系统触发的事件生成的触发消息。<br /> </td> 
   <td> 营销<br /> </td> 
   <td> 可选，了 <a href="../../message-center/using/about-transactional-messaging.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 事务性消息执行（消息中心——执行） <br /> </td> 
   <td> 确保更高的可用性和更好的负载管理。<br /> </td> 
   <td> 执行<br /> </td> 
   <td> 可选，了 <a href="../../message-center/using/about-transactional-messaging.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 线渠道<br /> </td> 
   <td> 使用带有Adobe Campaign的LINE渠道发送投放,<br /> </td> 
   <td> 所有<br /> </td> 
   <td> 可选，必填消息中心</td> 
  </tr> 
  <tr> 
   <td> 直邮渠道<br /> </td> 
   <td> 使用带有Adobe Campaign的直邮渠道发送投放。<br /> </td> 
   <td> 所有<br /> </td> 
   <td> 可选，了 <a href="../../delivery/using/about-direct-mail-channel.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 移动渠道(SMS) <br /> </td> 
   <td> 使用带Adobe Campaign的移动/SMS渠道发送投放。<br /> </td> 
   <td> 所有<br /> </td> 
   <td> 可选，了 <a href="../../delivery/using/sms-channel.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 电话渠道<br /> </td> 
   <td> 使用带Adobe Campaign的电话渠道发送投放。<br /> </td> 
   <td> 所有<br /> </td> 
   <td> 可选</td> 
  </tr> 
  <tr> 
   <td> 传真渠道<br /> </td> 
   <td> 使用带有Adobe Campaign的传真渠道发送投放。<br /> </td> 
   <td> 所有<br /> </td> 
   <td> 可选</td> 
  </tr> 
  <tr> 
   <td> 移动应用程序渠道<br /> </td> 
   <td> 使用Adobe Campaign平台通过应用程序向iOS和Android终端发送个性化通知。 <br /> </td> 
   <td> 所有<br /> </td> 
   <td> 可选，了 <a href="../../delivery/using/about-mobile-app-channel.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 内容管理器<br /> </td> 
   <td> 创建经常性新闻稿或网站，然后验证并发布您的消息。<br /> </td> 
   <td> </td> 
   <td> <a href="../../delivery/using/about-content-management.md">了解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 在线调查(调查经理)<br /> </td> 
   <td> 创建和管理在线表单以添加或修改用户档案信息、订阅、取消订阅或竞争条目表单。<br /> </td> 
   <td> 营销<br /> </td> 
   <td> 可选，了 <a href="../../web/using/about-surveys.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> 使您能够分析和测量数据、计算统计数据、简化和优化报表创建和计算。 此外，您还可以创建报告并构建目标群。 <br /> </td> 
   <td> 营销<br /> </td> 
   <td> 可选，了 <a href="../../reporting/using/about-cubes.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 响应管理器<br /> </td> 
   <td> 衡量所有通信渠道的营销活动或优惠建议的成功和盈利能力。<br /> </td> 
   <td> 营销<br /> </td> 
   <td> 可选，了 <a href="../../campaign/using/about-response-manager.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 访问外部数据(联合数据访问)<br /> </td> 
   <td> Provides the Federated Data Access (FDA) option in order to process information stored in one or more external databases so that you can access external data without changing the structure of Adobe Campaign data.<br /> </td> 
   <td> 所有<br /> </td> 
   <td> 可选，了 <a href="../../workflow/using/accessing-an-external-database--fda-.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 活动优化<br /> </td> 
   <td> 控制、过滤器和监控投放的发送，以使发送的消息最符合客户的需求和期望，并符合公司通信策略。 <br /> </td> 
   <td> 营销<br /> </td> 
   <td> 可选，了 <a href="../../campaign/using/about-campaign-typologies.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 交付性监控（电子邮件交付性）<br /> </td> 
   <td> 衡量活动到达收件人收件箱的成功程度，而不会弹跳或标记为垃圾邮件。<br /> </td> 
   <td> 所有 </td> 
   <td> 可选，了 <a href="https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 优惠券管理<br /> </td> 
   <td> 创建一组优惠券，以添加到即将到来的营销优惠。<br /> </td> 
   <td> 营销<br /> </td> 
   <td> 可选，了 <a href="../../delivery/using/personalized-coupons.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 收件箱渲染(IR)<br /> </td> 
   <td> 使您能够预览在不同上下文中发送的消息，并检查主要桌面和应用程序的兼容性。 你需要个利特姆斯账户。<br /> </td> 
   <td> 营销<br /> </td> 
   <td> 可选，了 <a href="../../delivery/using/inbox-rendering.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 中央／本地营销(分布式营销)<br /> </td> 
   <td> 实施中央实体（总部、营销部门等）之间的合作活动和本地实体（销售点、区域代理等）。<br /> </td> 
   <td> 营销 </td> 
   <td> 可选，了 <a href="../../campaign/using/about-distributed-marketing.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> CRM连接器<br /> </td> 
   <td> Provides various CRM connectors for linking your Adobe Campaign platform to your third-party systems.<br /> </td> 
   <td> 营销</td> 
   <td> <a href="../../platform/using/crm-connectors.md">了解更多</a> </td> 
  </tr> 
  <tr> 
   <td> Web Analytics连接器<br /> </td> 
   <td> 允许Adobe Campaign和Adobe Analytics通过Web Analytics连接器包进行交互。<br /> </td> 
   <td> 营销 </td> 
   <td> 与交易消息不兼容，了解 <a href="../../platform/using/adobe-analytics-data-connector.md">更多</a> </td> 
  </tr> 
  <tr> 
   <td> AEM集成<br /> </td> 
   <td> 允许您直接在Adobe Experience Manager中管理电子邮件投放和表单的内容，以便从AEM的内容编辑功能以及Adobe Campaign的投放能力中获益。<br /> </td> 
   <td> 营销</td> 
   <td> <a href="../../integrations/using/about-adobe-experience-manager.md">了解更多</a> </td> 
  </tr> 
  <tr> 
   <td> Adobe Marketing Cloud共享受众集成<br /> </td> 
   <td> 允许您使用Adobe Experience Cloud解决方案和核心服务交换和共享受众/细分。<br /> </td> 
   <td> 营销<br /> </td> 
   <td> 需要IMS，了 <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 与Adobe Marketing Cloud集成<br /> </td> 
   <td> 使您能够从不同的Adobe Marketing Cloud解决方案将受众/区段导入和导出到Adobe Campaign中。 </td> 
   <td> 营销</td> 
   <td> 可选，了 <a href="../../integrations/using/configuring-ims.md#installing-the-package">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 隐私数据保护规定<br /> </td> 
   <td> 包含其他功能，可帮助您在Campaign Classic中遵守隐私权。<br /> </td> 
   <td> 所有</td> 
   <td> <a href="https://helpx.adobe.com/campaign/kb/acc-privacy.html">了解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 转让至中间源 <br /> </td> 
   <td> 详细说明中间源服务器的安装和配置以及允许第三方以中间源模式发送消息的实例的部署。<br /> </td> 
   <td> 营销 </td> 
   <td> 可选，了 <a href="../../installation/using/mid-sourcing-server.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> 中间源平台<br /> </td> 
   <td> 此配置是在托管(ASP)配置和内部化之间的最佳中间解决方案。 所述朝外执行组件在托管于Adobe Campaign的“中间源”服务器上执行。<br /> </td> 
   <td> 中间源 </td> 
   <td> 可选，了 <a href="../../installation/using/mid-sourcing-server.md">解更多</a> </td> 
  </tr> 
  <tr> 
   <td> ACS连接器<br /> </td> 
   <td> 桥接Adobe Campaignv7和Adobe Campaign标准版。 它是v7活动中的一项集成功能，可将数据自动复制到Campaign Standard中，从而将两种应用程序的最佳功能结合起来。 <br /> </td> 
   <td> 营销 </td> 
   <td> 可选，了 <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">解更多</a> </td> 
  </tr> 
 </tbody> 
</table>

### 消息中心包 {#message-center-package}

要添加投放渠道(移动渠道、移动应用渠道等)，必须在安装消息中心包之前执行此操作。 如果您已在电子邮件渠道中启动了消息中心项目，那么在项目中间，您决定添加新渠道，则必须执行以下步骤：

1. 使用包渠道()安装 **Mobile渠道**，例如安装Mobile导入向导 **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**。
1. 导入文件( **[!UICONTROL Tools > Advanced > Import package > File]**)，然后选择：

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. 在中， **[!UICONTROL XML data content to import]**&#x200B;仅保留与附加的投放模板对应的消息中心渠道。 例如，如果您已添加 **Mobile渠道**，则只保留与(smsTriggerMessage)模板对应的 **entities****[!UICONTROL Mobile transactional message]** 元素。 如果已添加“移动应 **用程序渠道**”，则仅保留 **iOS事务性消息模板(iosTriggerMessage)和** Android事务性消息 **** (androidTriggerMessage)。

   ![](assets/messagecenter_install_channel.png)

### LINE包 {#line-package}

要能够使用带Adobe Campaign的LINE渠道发送投放，必须安装LINE包。

安装LINE包是标准安装，详见“导入包” [一节](../../platform/using/working-with-data-packages.md#importing-packages) 。

![](assets/line_config_1.png)

>[!CAUTION]
>
>如果在LINE之前安装了Message Center包，则LINE的Message Center投放模板将不可用。
