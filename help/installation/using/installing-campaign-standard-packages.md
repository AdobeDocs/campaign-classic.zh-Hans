---
product: campaign
title: 安装Campaign Classic内置软件包
description: 了解如何安装Campaign内置软件包
feature: Installation, Application Settings
badge-v7-prem: label="仅限内部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hans" tooltip="仅适用于内部部署和混合部署"
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1264'
ht-degree: 2%

---

# 安装Campaign Classic内置软件包{#installing-campaign-standard-packages}



## 关于内置软件包 {#campaign-standard-packages}

内置软件包包含一系列功能，可以根据您的需求和合同进行安装。 下面提供了Campaign内置软件包的完整列表。

>[!CAUTION]
>
>您只能安装与许可协议中提到的选项对应的软件包。
>
>安装新包可能会影响您的所有平台：必须在最终部署之前测试和验证该包。
>
>软件包安装后，将无法卸载。
>
>作为托管或混合型客户，请联系Adobe以部署新的内置包。

要安装内置软件包，请执行以下操作：

1. 从Adobe Campaign客户端控制台的&#x200B;**[!UICONTROL Tools > Advanced > Import package]**&#x200B;访问包导入助手。
1. 选择 **[!UICONTROL Install a standard package]**。
1. 在包列表中，选中要安装的包。
   >[!NOTE]
   >
   >当包呈灰显状态时，表示已安装或与实例不兼容。 兼容性详见下表。
1. 单击&#x200B;**[!UICONTROL Next]**，然后单击&#x200B;**[!UICONTROL Start]**&#x200B;以开始安装包。

   安装包后，进度条显示&#x200B;**100%**，您可以在安装日志中看到以下消息： **[!UICONTROL Installation of packages successful]**。

1. **[!UICONTROL Close]**&#x200B;安装窗口。

包现已安装。

### 现成软件包列表 {#list-of-standard-packages}

下表列出了所有Campaign内置软件包。

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
   <td> 监视投放以及在发送消息时遇到的最终问题。 <a href="../../delivery/using/about-delivery-monitoring.md">了解详情</a><br /> </td> 
   <td> 全部</td> 
  </tr> 
  <tr> 
   <td> 营销活动（营销活动）<br /> </td> 
   <td> 定义、优化、执行和分析通信和营销活动。 <a href="../../campaign/using/designing-marketing-campaigns.md">了解更多</a><br /> </td> 
   <td> 营销</td>
  </tr> 
  <tr> 
   <td> 营销资源(MRM)<br /> </td> 
   <td> 通过提供对任务、预算和营销资源的管理和跟踪，在协作模式下控制营销活动。 <a href="../../mrm/using/about-marketing-resource-management.md">了解更多</a> <br /> </td> 
   <td> 营销</td> 
  </tr> 
  <tr> 
   <td> 优惠引擎（交互）<br /> </td> 
   <td> 在与给定联系人（客户或目标）交互期间通过使其成为单个或数个自适应优惠实时响应。  可选。 <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 使用执行实例控制优惠引擎。 可选。<br /> </td> 
   <td> 要在选件引擎的控制实例上安装的包（交互）。 <a href="../../interaction/using/distributed-architectures.md#packages-configuration">了解更多</a> </td> 
   <td> 营销<br /> </td>  
  </tr> 
  <tr> 
   <td> 执行实例的优惠引擎。 可选。<br /> </td> 
   <td> 要在优惠引擎（交互）的执行实例上安装的包。 <a href="../../interaction/using/distributed-architectures.md">了解更多</a> </td> 
   <td> 中间，执行<br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> 社交网络（社交营销） <br /> </td> 
   <td> 将Adobe Campaign与X(以前称为Twitter)和Facebook同步。 <a href="../../social/using/about-social-marketing.md">了解更多</a> <br /> </td> 
   <td> 全部</td> 
  </tr> 
  <tr> 
   <td> 事务性消息控制（消息中心 — 控制）<br /> </td> 
   <td> 管理从信息系统触发的事件生成的触发消息。 可选。 <a href="../../message-center/using/about-transactional-messaging.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 事务性消息执行（消息中心 — 执行） <br /> </td> 
   <td> 确保更高的可用性和更好的负载管理。 可选。 <a href="../../message-center/using/about-transactional-messaging.md">了解更多</a><br /> </td> 
   <td> 执行<br /> </td>
  </tr> 
  <tr> 
   <td> LINE频道<br /> </td> 
   <td> 在Adobe Campaign中使用LINE渠道发送投放。 可选。 事务性消息传递（消息中心包）是必需的。 <a href="../../delivery/using/line-channel.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 直邮渠道<br /> </td> 
   <td> 在Adobe Campaign中使用直邮渠道发送投放。 可选。 <a href="../../delivery/using/about-direct-mail-channel.md">了解更多</a><br /> </td> 
   <td> 所有<br /> </td>
  </tr> 
  <tr> 
   <td> 移动渠道（短信）<br /> </td> 
   <td> 使用带有Adobe Campaign的移动/短信渠道发送投放。 可选。 <a href="../../delivery/using/sms-channel.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
   <tr> 
   <td> 电话渠道<br /> </td> 
   <td> 在Adobe Campaign中使用电话渠道发送投放。 用于呼叫中心。 可选。 <a href="../../delivery/using/communication-channels.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 移动应用频道<br /> </td> 
   <td> 使用Adobe Campaign平台通过应用程序向iOS和Android终端发送个性化通知。 可选。 <a href="../../delivery/using/about-mobile-app-channel.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 内容管理器<br /> </td> 
   <td> 创建定期新闻稿或网站，然后验证并发布消息。 <a href="../../delivery/using/about-content-management.md">了解更多</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> 在线调查（调查管理器）<br /> </td> 
   <td> 创建和管理在线表单，以添加或修改用户档案信息、订阅、取消订阅或竞争登录表单。 可选。 <a href="../../surveys/using/about-surveys.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> 用于分析和测量数据、计算统计数据、简化和优化报告创建和计算。 此外，您还可以创建报告并构建目标群体。 可选。 <a href="../../reporting/using/ac-cubes.md">了解更多</a><br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 响应管理器<br /> </td> 
   <td> 衡量营销活动的成功性和盈利能力，或为所有通信渠道提供建议。  可选。 <a href="../../response/using/about-response-manager.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 访问外部数据（联合数据访问）<br /> </td> 
   <td> 提供联合数据访问(FDA)选项，以处理存储在一个或多个外部数据库中的信息，以便您能够访问外部数据而不改变Adobe Campaign数据的结构。  可选。 <a href="../../workflow/using/accessing-an-external-database-fda.md">了解更多</a> <br /> </td> 
   <td> 所有<br /> </td> 
  </tr> 
  <tr> 
   <td> 营销活动优化<br /> </td> 
   <td> 控制、过滤和监控投放的发送，以使发送的消息最符合客户的需要和期望，同时遵守公司的通信政策。 可选。 <a href="../../campaign-opt/using/about-campaign-typologies.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 可投放性监控（电子邮件可投放性）<br /> </td> 
   <td> 衡量营销活动在未退回或标记为垃圾邮件的情况下到达收件人的收件箱是否成功。 可选。 <a href="../../delivery/using/about-deliverability.md">了解更多</a> <br /> </td> 
   <td> 全部 </td> 
  </tr> 
  <tr> 
   <td> 优惠券管理<br /> </td> 
   <td> 创建一组优惠券以添加到即将推出的营销优惠中。 可选。 <a href="../../delivery/using/personalized-coupons.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 收件箱呈现(IR)<br /> </td> 
   <td> 允许您预览在可能接收消息的不同上下文中发送的消息，并检查主要桌面和应用程序中的兼容性。 可选。 <a href="../../delivery/using/inbox-rendering.md">了解更多</a><br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 中央/本地营销（分布式营销）<br /> </td> 
   <td> 实施中央实体（总部、营销部门等）与地方实体（销售点、区域机构等）之间的合作活动。 可选。 <a href="../../distributed/using/about-distributed-marketing.md">了解更多</a><br /> </td> 
   <td> 营销 </td> 
  </tr> 
  <tr> 
   <td> CRM 连接器<br /> </td> 
   <td> 提供各种CRM连接器，用于将您的Adobe Campaign平台链接到第三方系统。  <a href="../../platform/using/crm-connectors.md">了解更多</a> <br /> </td> 
   <td> 营销</td> 
  </tr> 
  <tr> 
   <td> 网站分析连接器<br /> </td> 
   <td> 允许Adobe Campaign和Adobe Analytics通过Web Analytics连接器包进行交互。 与事务性消息传递（消息中心包）不兼容。 <a href="../../integrations/using/gs-aa.md">了解更多</a><br /> </td> 
   <td> 营销 </td> 
  </tr> 
  <tr> 
   <td> AEM集成<br /> </td> 
   <td> 允许您直接在Adobe Experience Manager中管理电子邮件投放和表单的内容，以便从AEM的内容编辑功能以及Adobe Campaign的投放功能中受益。 <a href="../../integrations/using/about-adobe-experience-manager.md">了解更多</a> <br /> </td> 
   <td> 营销</td> 
  </tr> 
  <tr> 
   <td> Adobe Experience Cloud共享受众集成<br /> </td> 
   <td> 允许您与Adobe Experience Cloud解决方案和应用程序交换和共享受众/区段。 需要IMS。 <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">了解更多</a> <br /> </td> 
   <td> 营销<br /> </td> 
  </tr> 
  <tr> 
   <td> 与Adobe Experience Cloud<br />集成 </td> 
   <td> 允许您将受众/区段从不同的Adobe Experience Cloud解决方案导入和导出到Adobe Campaign中。 可选。 <a href="../../integrations/using/configuring-ims.md#installing-the-package">了解更多</a> </td> 
   <td> 营销</td> 
  </tr> 
  <tr> 
   <td> 隐私数据保护条例<br /> </td> 
   <td> 包含可帮助在Campaign Classic中遵守隐私规定的其他功能。 <a href="https://helpx.adobe.com/cn/campaign/kb/acc-privacy.html">了解更多</a> <br /> </td> 
   <td> 全部</td> 
  </tr> 
  <tr> 
   <td> 传输到中间源<br /> </td> 
   <td> 详细介绍中间源服务器的安装和配置，以及使第三方能够在中间源模式下发送消息的实例的部署。 可选。 <a href="../../installation/using/mid-sourcing-server.md">了解更多</a> <br /> </td> 
   <td> 营销 </td> 
  </tr> 
  <tr> 
   <td> 中间源平台<br /> </td> 
   <td> 此配置是托管(ASP)配置与内部化之间的最佳中间解决方案。 在Adobe Campaign托管的“中间源”服务器上执行面向外部的执行组件。 可选。 <a href="../../installation/using/mid-sourcing-server.md">了解更多</a> <br /> </td> 
   <td> 中间源 </td> 
  </tr> 
  <tr> 
   <td> AMP支持<br /> </td> 
   <td> 使您能够使用新的交互式AMP作为电子邮件格式，并发送动态电子邮件。 可选。 <a href="../../delivery/using/defining-interactive-content.md">了解更多</a> <br /> </td> 
   <td> 全部 </td> 
  </tr> 
  <tr> 
   <td> ACS连接器（已弃用）<br /> </td> 
   <td> 桥接器Adobe Campaign v7和Adobe Campaign Standard。 它是Campaign v7中的一项集成功能，可自动将数据复制到Campaign Standard，将两个应用程序的优点结合起来。 可选。<br /> </td> 
   <td> 营销 </td> 
  </tr> 
 </tbody> 
</table>

### 消息中心包 {#message-center-package}

在安装事务性消息（消息中心包）之前，必须安装投放渠道（电子邮件、移动渠道、移动应用程序渠道、LINE等）。 如果您已启动仅用于电子邮件的消息中心项目，并且以后需要添加新渠道，则必须执行以下步骤：

1. 使用包导入助手(**[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**)安装新频道，例如&#x200B;**Mobile频道**。
1. 导入文件( **[!UICONTROL Tools > Advanced > Import package > File]**)，然后选择：

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. 在&#x200B;**[!UICONTROL XML data content to import]**&#x200B;中，仅保留与相关渠道对应的消息中心投放模板。 例如，如果您已添加&#x200B;**移动渠道**，则仅保留与&#x200B;**[!UICONTROL Mobile transactional message]** (smsTriggerMessage)模板对应的&#x200B;**实体**&#x200B;元素。 如果您已添加&#x200B;**移动应用程序渠道**，请仅保留&#x200B;**iOS事务型消息**&#x200B;模板(iosTriggerMessage)和&#x200B;**Android事务型消息** (androidTriggerMessage)。

   ![](assets/messagecenter_install_channel.png)


### [!DNL LINE]渠道设置{#line-package}

要设置[!DNL LINE]渠道，必须先安装[!DNL LINE]包。

在中间源配置的上下文中，您需要：

* 在营销和MID实例上安装[!DNL LINE]包

* 在mkt实例上设置[!DNL LINE]外部帐户，以通过更改传递模式指向mid实例。 [了解详情](../../delivery/using/line-channel.md#configure-line-external)

* 在MID实例的外部帐户中设置[!DNL LINE]凭据。

>[!CAUTION]
>
>如果消息中心包在[!DNL LINE]之前安装，[!DNL LINE]渠道的消息中心投放模板将不可用。