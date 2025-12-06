---
product: campaign
title: 高级 — 自定义投放日志
description: 了解如何扩展投放日志模式以在Campaign Classic v7中添加自定义字段
feature: Monitoring
role: User, Developer
exl-id: 44ecc8c6-6584-43eb-96b4-7d8463053123
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 1%

---

# 高级：自定义投放日志 {#customize-delivery-logs}

>[!NOTE]
>
>[Campaign v8文档](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/monitor/delivery-dashboard)中记录了有关访问投放列表和使用投放仪表板的全面指南。 此内容适用于Campaign Classic v7和Campaign v8用户。
>
>本页介绍了针对混合部署和内部部署的特定于&#x200B;**Campaign Classic v7的高级自定义项**。

要在Campaign UI中监视投放，请参阅Campaign UI文档中的[Campaign v8监视器投放](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}。

## 自定义投放日志 {#use-case}

对于&#x200B;**Campaign Classic v7混合/内部部署**，您可以通过扩展架构来自定义投放日志。 此部分说明如何将发件人的IP地址添加到投放日志。

>[!NOTE]
>
>此自定义需要内部部署中可用的架构扩展功能。 Campaign v8托管云服务用户应联系Adobe客户关怀团队，以获取自定义投放日志字段。
>
>如果您使用的是单个实例或中间源实例，则此修改会有所不同。 在执行修改之前，请确保已连接到电子邮件发送实例。

### 第1步：扩展模式

要在投放日志中添加&#x200B;**publicID**，您需要先扩展架构。 您可以按照以下步骤继续操作。

1. 在&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**&#x200B;下创建架构扩展。

   有关架构扩展的详细信息，请参阅[此页面](../../configuration/using/extending-a-schema.md)。

1. 选择&#x200B;**[!UICONTROL broadLogRcp]**&#x200B;以扩展收件人投放日志(nms)并定义自定义命名空间。 在本例中，它将为“cus”：

   ![](assets/schema-parameters.png)

   >[!NOTE]
   >
   >如果您的实例位于中间源中，则需要使用broadLogMid架构。

1. 在扩展中添加新字段。 在此示例中，您需要替换：

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp"/>
   ```

   通过：

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp">
   <attribute desc="Outbound IP identifier" label="IP identifier"
   name="publicId" type="long"/>
   </element>
   ```

   ![](assets/edit-schema.png)

### 步骤2：更新数据库结构

完成修改后，您需要更新数据库结构，以便使其与其逻辑描述保持一致。

为此请执行以下操作步骤：

1. 单击&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]**&#x200B;菜单。

   ![](assets/update-database-structure.png)

1. 在&#x200B;**[!UICONTROL Edit tables]**&#x200B;窗口中，已选中&#x200B;**[!UICONTROL NmsBroadLogRcp]**&#x200B;表（或者&#x200B;**[!UICONTROL broadLogMid]**&#x200B;表，如果您的表位于中间源环境中），如下所示：

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >始终确保除了&#x200B;**[!UICONTROL NmsBroadLoGRcp]**&#x200B;表(或者&#x200B;**[!UICONTROL broadLogMid]**&#x200B;表（如果您的表位于中间源环境中）之外，没有其他修改。 如果是，则取消选中其他表。

1. 单击&#x200B;**[!UICONTROL Next]**&#x200B;进行验证。 将显示以下屏幕：

   ![](assets/update-script.png)

1. 单击&#x200B;**[!UICONTROL Next]**，然后单击&#x200B;**[!UICONTROL Start]**&#x200B;以开始更新数据库结构。 正在开始索引生成。 此步骤可能很长，具体取决于&#x200B;**[!UICONTROL NmsBroadLogRcp]**&#x200B;表中的行数。

   ![](assets/start-database-update.png)

>[!NOTE]
>
>成功更新数据库的物理结构后，需要断开并重新连接，以便考虑所做的修改。

### 步骤3：验证修改

要确认所有组件正常工作，您需要更新投放日志屏幕。

为此，请访问投放日志并添加“IP标识符”列。

![](assets/list-config.png)

>[!NOTE]
>
>要了解如何在Campaign Classic界面中配置列表，请参阅[此页面](../../platform/using/adobe-campaign-workspace.md)。

以下是修改后您应在&#x200B;**[!UICONTROL Delivery]**&#x200B;选项卡中看到的内容：

![](assets/logs-with-ip.png)

## 相关主题

* [在Campaign UI中监视投放](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}（Campaign v8文档）
* [投放状态](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"}（Campaign v8文档）
* [了解投放失败](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"}（Campaign v8文档）
* [隔离管理](https://experienceleague.adobe.com/zh-hans/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"}（Campaign v8文档）
* [扩展架构](../../configuration/using/extending-a-schema.md)（v7混合/内部部署）

