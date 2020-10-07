---
title: 安装 Campaign Classic 标准包
seo-title: 安装 Campaign Classic 标准包
description: 安装 Campaign Classic 标准包
seo-description: null
page-status-flag: never-activated
uuid: 1cba9487-52fc-442f-ae99-f8a2c157f25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: dd8f9adf-208c-42d9-b1a7-bfc8a690687e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 6%

---


# Installing Campaign Classic built-in packages{#installing-campaign-standard-packages}

## 关于内置包 {#campaign-standard-packages}

内置软件包包含一组功能，这些功能可以根据您的需要并根据您的合同进行安装。 下面提供完整的活动内置包列表。

>[!CAUTION]
>
>您只能安装与许可协议中所述选项对应的软件包。
>
>安装新包可能会影响您的所有平台：它必须经过测试和验证，然后才能进行最终部署。
>
>安装包后，将无法卸载它。

安装内置包：

1. 从导入向导客户端控制台 **[!UICONTROL Tools > Advanced > Package import...]** 中访问包Adobe Campaign。
1. 选择 **[!UICONTROL Install a standard package]**。
1. 在包列表中，检查要安装的包。
   >[!NOTE]
   >
   >当包灰显时，表示它已安装或与实例不兼容。 兼容性详见下表。
1. 单 **[!UICONTROL Next]**&#x200B;击，然 **[!UICONTROL Start]** 后开始包安装。

   安装包后，进度栏显示 **100%** ，您可以在安装日志中看到以下消息： **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** 安装窗口。

软件包现在已安装。

### 列表现成包 {#list-of-standard-packages}

下表列表了所有标准包及其说明、可安装的实例类型（Marketing、Mid等）。 和其他信息。

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
   <td> 监视投放以及发送消息时遇到的最终问题。 <a href="../../delivery/using/monitoring-a-delivery.md">了解详情</a><br /> </td> 
   <td> 所有</td> 
  </tr> 
  <tr> 
   <td> 营销活动(活动)<br /> </td> 
   <td> 定义、优化、执行和分析通信和营销活动。 <a href="../../campaign/using/designing-marketing-campaigns.md">了解更多</a><br /> </td> 
   <td> 营销</td>
  </tr> 
  <tr> 
   <td> Marketing resources (MRM)<br /> </td> 
   <td> 通过提供对任务、预算和营销资源的管理和跟踪，以协作模式控制营销活动。 <a href="../../campaign/using/about-marketing-resource-management.md">了解更多</a> <br /> </td> 
   <td> 营销</td> 
  </tr> 
  <tr> 
   <td> 优惠引擎（交互）<br /> </td> 
   <td> 在与给定联系人(客户或目标)的交互过程中，通过使其成为单个或多个调整的优惠进行实时响应。  可选。<a href="../../interaction/using/interaction-and-offer-management.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 控制优惠引擎和执行实例。 可选。<br /> </td> 
   <td> </td> 
   <td> 营销<br /> </td>  
  </tr> 
  <tr> 
   <td> 优惠引擎，执行实例。 可选。<br /> </td> 
   <td> </td> 
   <td> 执行中 <br /> </td>  
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
   <td> 事务性消息控制（消息中心——控制）<br /> </td> 
   <td> 管理从信息系统触发的事件生成的触发消息。 可选。<a href="../../message-center/using/about-transactional-messaging.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 事务性消息执行（消息中心——执行） <br /> </td> 
   <td> 确保更高的可用性和更好的负载管理。 可选。<a href="../../message-center/using/about-transactional-messaging.md">了解更多</a><br /> </td> 
   <td> 执行<br /> </td>
  </tr> 
  <tr> 
   <td> LINE 渠道<br /> </td> 
   <td> 使用带投放的LINE渠道发送Adobe Campaign。 可选。必填事务消息（消息中心包）。 <a href="../../delivery/using/line-channel.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 直邮渠道<br /> </td> 
   <td> 使用带有投放的直接邮件渠道发送Adobe Campaign。 可选。<a href="../../delivery/using/about-direct-mail-channel.md">了解更多</a><br /> </td> 
   <td> 所有<br /> </td>
  </tr> 
  <tr> 
   <td> 移动渠道(SMS) <br /> </td> 
   <td> 使用带Adobe Campaign的移动／短信渠道发送投放。 可选。<a href="../../delivery/using/sms-channel.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 移动应用程序渠道<br /> </td> 
   <td> 使用Adobe Campaign平台，通过应用程序向iOS和Android终端发送个性化通知。 可选。<a href="../../delivery/using/about-mobile-app-channel.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 内容管理器<br /> </td> 
   <td> 创建定期新闻稿或网站，然后验证和发布您的消息。 <a href="../../delivery/using/about-content-management.md">了解更多</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> 在线调查(调查经理)<br /> </td> 
   <td> 创建并管理在线表单，以添加或修改用户档案信息、订阅、取消订阅或竞赛条目表单。 可选。<a href="../../web/using/about-surveys.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> 使您能够分析和衡量数据、计算统计、简化和优化报表创建和计算。 此外，您还可以创建报告并构建目标群。 可选。<a href="../../reporting/using/about-cubes.md">了解更多</a><br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 响应管理器<br /> </td> 
   <td> 衡量营销活动或优惠建议对所有通信渠道的成功和盈利能力。  可选。<a href="../../campaign/using/about-response-manager.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 访问外部数据(联合数据访问)<br /> </td> 
   <td> 提供联合数据访问(联合数据访问)选项，以便处理存储在一个或多个外部数据库中的信息，以便您能够访问外部数据而不更改Adobe Campaign数据的结构。  可选。<a href="../../workflow/using/accessing-an-external-database--fda-.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 活动优化<br /> </td> 
   <td> 控制、过滤器和监控投放的发送，使发送的消息能够最好地满足客户的需求和期望，并符合公司通信策略。 可选。<a href="../../campaign/using/about-campaign-typologies.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 交付性监控（电子邮件交付性）<br /> </td> 
   <td> 衡量活动到达收件人收件箱的成功程度，而不会弹跳或标记为垃圾邮件。 可选。<a href="../../delivery/using/about-deliverability.md">了解更多</a> <br /> </td> 
   <td> 所有 </td> 
  </tr> 
  <tr> 
   <td> 优惠券管理<br /> </td> 
   <td> 创建一组优惠券，以添加到即将到来的营销优惠。 可选。<a href="../../delivery/using/personalized-coupons.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件箱渲染(IR)<br /> </td> 
   <td> 使您能够预览在不同上下文下发送的消息，并检查主要桌面和应用程序的兼容性。 可选。<a href="../../delivery/using/inbox-rendering.md">了解更多</a><br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 中央／本地营销(分布式营销)<br /> </td> 
   <td> 实施中央实体（总部、营销部门等）之间的合作活动 和本地实体（销售点、地区代理等）。 可选。<a href="../../campaign/using/about-distributed-marketing.md">了解更多</a><br /> </td> 
   <td> 营销 </td> 
  </tr> 
  <tr> 
   <td> CRM connectors<br /> </td> 
   <td> 提供各种CRM连接器，用于将Adobe Campaign平台关联到第三方系统。  <a href="../../platform/using/crm-connectors.md">了解更多</a> <br /> </td> 
   <td> 营销</td> 
  </tr> 
  <tr> 
   <td> Web分析连接器<br /> </td> 
   <td> 允许Adobe Campaign和Adobe Analytics通过Web Analytics连接器包进行交互。 与事务消息（消息中心包）不兼容。 <a href="../../platform/using/adobe-analytics-data-connector.md">了解更多</a><br /> </td> 
   <td> 营销 </td> 
  </tr> 
  <tr> 
   <td> AEM集成<br /> </td> 
   <td> 允许您直接在Adobe Experience Manager管理电子邮件投放的内容和表单，以从AEM内容编辑功能和Adobe Campaign的投放能力中受益。 <a href="../../integrations/using/about-adobe-experience-manager.md">了解更多</a> <br /> </td> 
   <td> 营销</td> 
  </tr> 
  <tr> 
   <td> Adobe Marketing Cloud共享受众集成<br /> </td> 
   <td> 允许您与Adobe Experience Cloud解决方案和核心服务交换和共享受众/细分。 需要IMS <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 与Adobe Marketing Cloud集成<br /> </td> 
   <td> 使您能够将受众/细分从不同的Adobe Marketing Cloud解决方案导入和导出到Adobe Campaign。 可选。<a href="../../integrations/using/configuring-ims.md#installing-the-package">了解更多</a> </td> 
   <td> 营销</td> 
  </tr> 
  <tr> 
   <td> 隐私数据保护规定<br /> </td> 
   <td> 包含其他功能，可帮助您在Campaign Classic中遵守隐私。 <a href="https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html">了解更多</a> <br /> </td> 
   <td> 所有</td> 
  </tr> 
  <tr> 
   <td> Transfer to Mid-Sourcing <br /> </td> 
   <td> 详细说明中间源服务器的安装和配置以及允许第三方以中间源模式发送消息的实例的部署。 可选。<a href="../../installation/using/mid-sourcing-server.md">了解更多</a> <br /> </td> 
   <td> 营销 </td> 
  </tr> 
  <tr> 
   <td> 中间源平台<br /> </td> 
   <td> 此配置是托管(ASP)配置和内部化之间的最佳中间解决方案。 所述朝外执行组件在托管于Adobe Campaign的“中间源”服务器上执行。 可选。<a href="../../installation/using/mid-sourcing-server.md">了解更多</a> <br /> </td> 
   <td> 中间源 </td> 
  </tr> 
  <tr> 
   <td> ACS Connector<br /> </td> 
   <td> 桥梁Adobe Campaignv7和Adobe Campaign Standard。 它是v7活动中的一个集成功能，可自动将Campaign Standard复制到数据中，从而将两种应用程序的最佳结合起来。 可选。<a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">了解更多</a> <br /> </td> 
   <td> 营销 </td> 
  </tr> 
 </tbody> 
</table>

### 消息中心包 {#message-center-package}

您必须安装投放渠道(电子邮件、移动渠道、移动应用渠道等) 在安装Transactional Messaging（消息中心包）之前。 如果您已启动仅电子邮件消息中心项目，并且需要在之后添加新渠道，则必须执行以下步骤：

1. 使用包渠道()安 **装新导入向导**，例如Mobile **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**&#x200B;渠道。
1. 导入文件( **[!UICONTROL Tools > Advanced > Import package > File]**)，然后选择：

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. 在中， **[!UICONTROL XML data content to import]**&#x200B;仅保留与相关投放模板对应的消息中心渠道。 例如，如果已添加移动 **渠道**，则只保留与(smsTriggerMessage)模板 **对应的** entities元素 **[!UICONTROL Mobile transactional message]** 。 如果已添加“移 **动应用程序渠道**”，则只保留 **iOS事务性消息模板** (iosTriggerMessage)和 **Android事务性消息** (androidTriggerMessage)。

   ![](assets/messagecenter_install_channel.png)

>[!CAUTION]
>
>如果在LINE之前安装了Message Center包，则LINE的Message Center投放模板将不可用

