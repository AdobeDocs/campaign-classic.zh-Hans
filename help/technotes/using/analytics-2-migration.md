---
product: campaign
title: 迁移到Adobe Analytics 2.0 API
description: Campaign Classic - Adobe Analytics 2.0 API迁移指南
feature: Technote, Analytics Integration
hide: true
source-git-commit: 64460d51b002a7821bba9c2998d9ccccab3046ad
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 1%

---

# 迁移到Adobe Analytics 2.0 API {#analytics-2-migration}

Adobe Analytics 1.4 API的[生命周期即将结束](https://developer.adobe.com/analytics-apis/docs/1.4/guides/eol){target="_blank"}。 将Campaign实例链接到Adobe Analytics的[Web Analytics连接器](../../integrations/using/gs-aa.md)依赖于这些API，因此您需要升级到使用新Analytics 2.0 API的版本以保持集成运行。

>[!CAUTION]
>
>升级时会重新导入两个为连接器[!UICONTROL webAnalyticsSendMetrics]和[!UICONTROL webAnalyticsGetWebEvents]提供支持的内置技术工作流（请参阅[Web Analytics工作流参考](../../workflow/using/web-analytics.md)，了解每个工作流的用途）。 重新导入会覆盖您在这些工作流之上所做的任何自定义设置。 避免直接修改这些内置工作流 — 请改为在单独的自定义工作流中构建自定义项，以免将来升级时覆盖自定义项。 此升级还会更新内置Analytics JavaScript文件：如果您的任何自定义工作流引用这些文件，则这些文件将中断，需要适应新代码。

## 您是否受影响？ {#are-you-impacted}

如果您的实例将[!UICONTROL Web Analytics]外部帐户用于以下任意项目，则您会受到影响：

* 将电子邮件营销活动指标和属性作为指标发送到Adobe Analytics。
* 正在将分类数据发送到Adobe Analytics。
* 再营销流程（标识营销活动后转化的联系人）。
* 您计划首次配置的[!UICONTROL Web Analytics]外部帐户。

不确定其中哪一个适用于您？ 检查实例上活动的上述技术工作流，并在[!UICONTROL Administration > Platform > External accounts]中查看[!UICONTROL Web Analytics]外部帐户配置（请参阅[网站分析外部帐户](../../installation/using/external-accounts.md#web-analytics-external-account)）。

## 如何迁移 {#how-to-migrate}

如果您在&#x200B;**Adobe托管**&#x200B;实例上，Adobe会在升级过程中为您处理SFTP配置、IP允许列表和密钥配置 — 只需在新内部版本上线后验证用例即可。

如果您在&#x200B;**内部部署或混合**&#x200B;部署，请完成以下步骤。

1. [将您的Campaign环境](../../production/using/build-upgrade.md)升级到包含Adobe Analytics 2.0更改的版本。 您可以确认从[!UICONTROL Help > About...]运行哪个内部版本（请参阅[如何检查您的Campaign版本](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)）。
1. 查看上面哪些用例适用于您的实例，因为下一步取决于它。
1. 如果您使用再营销流程，则[!UICONTROL webAnalyticsFindConverted]工作流需要一个专用的SFTP渠道来与Adobe Analytics 2.0交换数据。 如下所示进行设置；否则，请跳至下一步。
   1. 使用基于密钥的身份验证为实例设置SFTP服务器，遵循您应应用于任何其他外部SFTP集成的相同[SFTP服务器最佳实践](../../platform/using/sftp-server-usage.md)。 Adobe提供了一个[示例SFTP安装脚本](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html?package=/content/software-distribution/en/details.html/content/dam/campaign/public/setup_sftp.zip){target="_blank"}来帮助您入门。
   1. 通过运行随新内部版本一起提供的脚本在Adobe Analytics中注册该服务器的连接详细信息：

      ```
      nlserver javascript -instance:<instance_name> -arg:host=<sftp_host_url>#user=<sftp_user> -file <path_to_the_file>/aaremarketingLocation.js
      ```

      示例：

      ```
      nlserver javascript -instance:test_mkt_stage2 -arg:host=test-mkt-stage1.campaign.adobe.com#user=test -file ./nl6/datakit/nms/eng/js/aaremarketingLocation.js
      ```

   1. 在SFTP服务器上将Adobe Analytics添加到允许列表，因为再营销导出仅从一组固定的Adobe IP范围启动：
      * [查找当前的Adobe Analytics数据收集IP地址](https://experienceleague.adobe.com/en/docs/core-services/interface/data-collection/ip-addresses){target="_blank"}，并将其添加到您的SFTP服务器的允许列表。 基于FTP的Analytics导出（包括数据馈送）仅源自伦敦、俄勒冈和新加坡地区的IPv4地址。
      * [检索Adobe Analytics公共密钥](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-18141){target="_blank"}并将其添加到SFTP服务器上的`authorized_keys`文件中，以便Analytics能够进行身份验证。
1. 通过在Campaign Explorer树中的&#x200B;**[!UICONTROL Administration]> [!UICONTROL Platform] >[!UICONTROL Options]**&#x200B;下创建或将选项的`longvalue`设置为[!UICONTROL xtkOption]中的`1`，在实例上启用`FEATUREFLAG_USE_ANALYTICS_20_API`功能标记。 无论上述哪种用例适用于您，都需要执行此步骤。
1. 在停用任何旧连接之前，通过实施适用于您的实例的每个用例来验证迁移(发送测试活动，检查指标是否进入Analytics，并确认再营销数据（如果适用）)。

## 设置新的网站分析外部帐户 {#setting-up-a-new-web-analytics-external-account}

无论您的实例是Adobe托管实例还是内部部署/混合实例，以下内容均适用。

如果您是首次配置[!UICONTROL Web Analytics]外部帐户，而不是迁移现有帐户，请按照[外部帐户设置步骤](../../installation/using/external-accounts.md#web-analytics-external-account)和[连接器入门指南](../../integrations/using/gs-aa.md)操作。

由于Analytics 2.0引入了新的分类处理方式，因此您还需要在Adobe Analytics中创建分类集，然后外部帐户才能提取报表包的分类数据。 这是一个新步骤：在配置转化变量和成功事件之后，在Campaign中配置外部帐户之前创建它。

要创建分类集，请执行以下操作：

1. 从[!DNL Adobe Analytics]顶部菜单栏中选择&#x200B;**[!UICONTROL Components]** > **[!UICONTROL Classification sets]**，然后单击&#x200B;**[!UICONTROL New]**。

   ![](assets/analytics-classification-set-menu.png)

1. 在&#x200B;**[!UICONTROL Add New Classification Set]**&#x200B;对话框中：

   ![](assets/analytics-classification-set-dialog.png)

   * 输入分类集的&#x200B;**[!UICONTROL Name]**。
   * 将&#x200B;**[!UICONTROL Type]**&#x200B;设置为&#x200B;**[!UICONTROL Primary]**。
   * 在&#x200B;**[!UICONTROL Job notifications]**&#x200B;中，选择分类集作业成功或失败时应通知的人员，并提供相应的电子邮件地址。
   * 在&#x200B;**[!UICONTROL Subscriptions]**&#x200B;中，选择您的报表包以及您在上一步中为内部营销活动名称创建的转化变量。

1. 单击 **[!UICONTROL Save]**。

在下一步配置外部帐户时，Campaign将自动搜索此分类集。 有关分类集的详细信息，请参阅[Adobe Analytics文档](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/create-set){target="_blank"}。

## 是否需要帮助？ {#need-help}

如果您在迁移期间遇到问题，请联系[Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}。
