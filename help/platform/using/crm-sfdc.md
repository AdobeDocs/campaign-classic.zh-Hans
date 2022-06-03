---
product: campaign
title: Campaign - Salesforce CRM连接器
description: 了解如何连接Campaign和Salesforce
feature: Salesforce Integration
exl-id: 94a1f00d-e952-4edd-9012-f71c87b897ca
source-git-commit: 9a6010d824794b01224f40bb2912a9a80fc0fb88
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 连接Campaign和Salesforce.com{#connect-to-sfdc}

![](../../assets/v7-only.svg)

在本页中，您将学习如何将Campaign Classic连接到 **Salesforce**.

数据同步是通过专用的工作流活动执行的。 [了解详情](../../platform/using/crm-data-sync.md)。


利用外部帐户，可将Salesforce数据导入和导出到Adobe Campaign。
要配置CRM Connector for Salesforce，请执行以下步骤：

1. 通过 **[!UICONTROL Administration > Platform > External accounts]** Adobe Campaign树的节点。
1. 选择 **[!UICONTROL Salesforce.com]**。
1. 输入设置以启用连接。

   ![](assets/ext_account_17.png)

   要配置Salesforce CRM外部帐户以与Adobe Campaign配合使用，您需要提供以下详细信息：

   * **[!UICONTROL Account]**
用于登录到Salesforce CRM的帐户。

   * **[!UICONTROL Password]**
用于登录到Salesforce CRM的密码。

   * **[!UICONTROL Client identifier]**
要了解在何处查找客户端标识符，请参阅 [页面](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL Security token]**
要了解在何处查找安全令牌，请参阅此 [页面](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

   * **[!UICONTROL API version]**
选择API的版本。
1. 运行配置向导以生成可用的CRM表：通过配置向导，您可以收集表并创建匹配的架构。

   ![](assets/crm_connectors_sfdc_launch.png)

   >[!NOTE]
   >
   >要批准该设置，您需要注销并重新启动Adobe Campaign控制台。

1. 检查在Adobe Campaign中生成的架构(位于 **[!UICONTROL Administration > Configuration > Data schemas]** 节点。

   示例 **Salesforce** 架构：

   ![](assets/crm_connectors_sfdc_table.png)

1. 创建架构后，您可以自动将枚举从Salesforce同步到Adobe Campaign。

   为此，请单击 **[!UICONTROL Synchronizing enumerations...]** 链接并选择与Salesforce枚举匹配的Adobe Campaign枚举。



   ![](assets/crm_connectors_sfdc_enum.png)

   >[!NOTE]
   >
   >您可以将Adobe Campaign枚举的所有值替换为CRM的值：要执行此操作，请选择 **[!UICONTROL Yes]** 在 **[!UICONTROL Replace]** 列。


   单击 **[!UICONTROL Next]** 然后 **[!UICONTROL Start]** 开始导入列表。

1. 检查 **[!UICONTROL Administration > Platform > Enumerations]** 菜单。

   ![](assets/crm_connectors_sfdc_exe.png)

   >[!NOTE]
   >
   > 不支持多个选择枚举。

Campaign和Salesforce.com现已连接。 您可以在两个系统之间设置数据同步。

要在Adobe Campaign数据和SFDC之间同步数据，您需要创建一个工作流，并使用 **[!UICONTROL CRM connector]** 活动。

![](assets/crm_connectors_sfdc_wf.png)

了解有关数据同步的更多信息 [本页](../../platform/using/crm-data-sync.md).
